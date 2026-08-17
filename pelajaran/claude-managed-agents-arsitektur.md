# Claude Managed Agents — arsitektur & kode implementasi (Anthropic)

**Sumber:** `D:\Downloads\Tiburon\03-hasil-analisis\analisis-video.md`, entri
video `aiagnetclaude.mp4` — talk + hands-on workshop **"Ship your first
Managed Agent"** oleh **Isabella He** (Member of Technical Staff, Anthropic,
Applied AI team), event Code w/ Claude. Repo workshop resmi:
`github.com/anthropics/cwc-workshops/ship-your-first-managed-agent`.
Referensi implementasi paling konkret dan langsung-bisa-dipakai sejauh ini
di Tiburon untuk membangun agent produksi di atas Claude Managed Agents API
— bukan cuma konsep, kode Python nyata untuk 7 fungsi inti. Lihat juga
[arsitektur-memori-agent-anthropic.md](arsitektur-memori-agent-anthropic.md)
— talk lain dari acara yang sama, tentang fitur memory & dreaming yang
disebut sebagai bagian dari "Beyond the basics" di talk ini.

## Evolusi 3 interface untuk membangun agent

1. **Messages API** (2023) — akses model mentah. Kamu kelola semua: agent
   loop + context management, tool execution runtime, session state &
   recovery, hosting/auth/observability, custom tool logic.
2. **Agent SDK** — harness pembungkus Claude Code sebagai library. Kamu
   masih kelola hosting & scaling, session state/auth/observability, custom
   tool logic (MCP). SDK menangani agent loop + context mgmt (caching,
   compaction), built-in tool execution + retries.
3. **Managed Agents** (state-of-the-art) — kamu cuma sediakan task + agent
   config, custom tool logic (MCP/Skills). Anthropic menangani sisanya:
   purpose-built harness + context mgmt, tool runtime & sandbox, session
   persistence & checkpointing, auth (OAuth) + credential vault, hosting/
   scaling/observability. Klaim: 10-15× lebih cepat ke produksi.

## 3 resource utama

1. **`/v1/agents`** — persona + capabilities (model, system prompt, tools,
   MCP servers, skills). Versioned & immutable.
2. **`/v1/environments`** — infrastructure + guardrails (container config,
   networking allow-list). Set up once, reuse everywhere.
3. **`/v1/sessions`** — pair agent + environment, mulai satu interaksi,
   stream events, bisa di-resume kapan saja.

## Prinsip arsitektur inti

- **Agent loop berjalan server-side** — orchestration (tool calls, retries,
  context management) hidup di infrastruktur Anthropic, bukan di client.
- **"The brain left the box"** — pemisahan arsitektur: brain (agent loop,
  dikelola Anthropic, satu service untuk ribuan sesi, survive crash) vs
  hands (sandbox, provisioned on-demand cuma saat tool dipanggil). Manfaat
  konkret: keamanan credential (agent tidak bisa akses kredensial tanpa
  enkripsi) dan latency (>90% reduction TTFT p95 vs container-per-sesi).
- **Sessions bicara dalam events, bukan request/response** — event
  di-append ke log sesi (gampang di-resume, gampang diobservasi). Kalau
  container mati, cukup restart container-nya, bukan seluruh agent loop.
  - Events yang dikirim (`POST /v1/sessions/{id}/events`): `user.message`,
    `user.custom_tool_result`, `user.tool_confirmation`, `user.interrupt`.
  - Events yang diterima (`GET /v1/sessions/{id}/stream`): `agent.message`,
    `agent.tool_use`, `agent.custom_tool_use`, `agent.mcp_tool_use`,
    `session.status_idle`, `session.error`.
- **Tool custom dieksekusi lokal** — tidak ada inbound networking, klien
  yang tahan pipa (SSE stream) terbuka, request "menumpang" balik lewat
  situ. Swap sumber data lokal (`json.load(...)`) ke sistem produksi (mis.
  Datadog) itu wire-protocol yang sama, gampang dipindah tanpa ubah desain.
- **Percakapan hidup di cloud** — histori sesi persisten di server
  Anthropic; hard refresh browser tidak menghilangkan sesi.

## 7 fungsi inti untuk membangun agent (`agent.py`)

```python
# 1. Definisikan persona + capabilities
@st.cache_resource
def setup_agent() -> str:
    agent = client.beta.agents.create(
        name="SRE Agent", model="claude-opus-4-7", system=SYSTEM, tools=TOOLS,
    )
    return agent.id

# 2. Definisikan infrastruktur + guardrail jaringan
@st.cache_resource
def setup_environment() -> str:
    env = client.beta.environments.create(
        name=f"sre-agent-{uuid.uuid4().hex[:6]}",
        config={"type": "cloud", "networking": {"type": "unrestricted"}},
    )
    return env.id

# 3. Upload data lewat Files API
@st.cache_resource
def upload_log() -> str:
    with open(DATA / "app.log", "rb") as f:
        return client.beta.files.upload(file=f).id

# 4. Bind agent + environment + mount data
def start_session(agent_id: str, env_id: str, log_file_id: str) -> str:
    session = client.beta.sessions.create(
        agent=agent_id,
        environment_id=env_id,
        resources=[{"type": "file", "file_id": log_file_id, "mount_path": "app.log"}],
    )
    return session.id

# 5. Buka stream, kirim pesan, jawab tool call inline
def stream_reply(session_id: str, user_text: str):
    with client.beta.sessions.events.stream(session_id) as stream:   # open first
        client.beta.sessions.events.send(session_id, events=[        # then send
            {"type": "user.message", "content": [{"type": "text", "text": user_text}]}
        ])
        for ev in stream:
            if ev.type == "agent.custom_tool_use":        # cloud → you
                result = handle_tool(ev.name, ev.input)
                client.beta.sessions.events.send(session_id, events=[   # you → cloud
                    {"type": "user.custom_tool_result",
                     "custom_tool_use_id": ev.id,
                     "content": [{"type": "text", "text": result}]}
                ])
            yield ev

# 6. Local tool handler
def handle_tool(name: str, args: dict) -> str:
    if name == "get_metrics":
        return json.dumps(metrics.get(args["service"], {})) or "..."
    if name == "get_recent_deploys":
        return deploys
    if name == "get_diff":
        return diff if args["commit"][:7] in diff else "no diff for that commit"
    return f"unknown tool {name}"

# 7. Bersihkan session (cloud resource nyata)
def delete_session(session_id: str) -> None:
    client.beta.sessions.delete(session_id)
```

Client: `anthropic.Anthropic()` (SDK Python resmi), namespace
`client.beta.agents` / `.environments` / `.sessions` / `.sessions.events` /
`.files`. Demo UI pakai **Streamlit** (`streamlit run app.py`).

## Fitur "Beyond the basics" (semua berlabel Beta)

Subagents (`callable_agents` — orchestrator + subagent, tiap subagent
punya context window sendiri) · Memory (persistent, di-mount ke container,
dipasangkan dengan dreaming — lihat
[arsitektur-memori-agent-anthropic.md](arsitektur-memori-agent-anthropic.md))
· Outcomes (artefak terstruktur + rubric hasil) · Vaults (kredensial
per-user, enkripsi via arsitektur brain/hands terpisah) · MCP servers ·
Webhooks (fires on `session.status_idled`) · Permission policies
(`always_ask` → pause, tunggu `user.tool_confirmation`) · Interrupt
(`user.interrupt` paksa agent idle) · Console agent builder.

## Kesalahan umum / peringatan desain

- **Jangan couple agent loop dengan tool execution di container yang sama**
  kalau butuh keamanan credential ketat atau latency rendah.
- **Harness yang di-hardcode untuk menambal perilaku model tertentu bisa
  usang.** Contoh nyata: mitigasi khusus ditambahkan untuk "context anxiety"
  Sonnet 4.5 (berhenti kerja lebih awal padahal context window masih ada
  ruang) — begitu Opus 4.5 rilis, perilaku itu hilang sendiri, mitigasi jadi
  sia-sia. Harness harus dirancang untuk **berevolusi**, bukan ditambal
  permanen untuk perilaku model versi tertentu.
- **Jangan lupa hapus session** — cloud resource nyata, ada implikasi
  data/privasi kalau dibiarkan.
- **Jangan default networking `unrestricted` di produksi** — field
  `networking` di environment config adalah allow-list, batasi ke host yang
  benar-benar dibutuhkan.
- **Konteks yang diberikan ke agent menentukan kualitas hasil** — bagian
  terbesar waktu developer bukan di primitif infrastruktur (sudah ditangani
  Managed Agents), tapi di context engineering: data apa yang di-upload,
  bagaimana agent memprosesnya.

## Cara pakai

Relevan kalau Shiftware (produk atau workflow internal) butuh membangun
agent otonom (mis. automasi customer support, monitoring, asisten internal)
di atas infrastruktur terkelola Anthropic, alih-alih membangun harness
sendiri dari nol via raw Messages API. Kode 7-fungsi di atas adalah
kerangka minimal yang bisa langsung dijadikan starting point.
