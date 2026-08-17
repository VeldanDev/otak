# Arsitektur memori AI agent — talk Anthropic (memory + dreaming)

**Sumber:** `D:\Downloads\Tiburon\03-hasil-analisis\analisis-video.md`, entri
video `aiyourpromt.mp4` — talk konferensi **AI DevCon by Tessl**, "Learning
while you Sleep — Beyond Memory to Dreaming" oleh **Lamis Mukta** (Member of
Technical Staff, Anthropic, tim Applied AI). Referensi arsitektur paling
mendalam dari sumber Anthropic langsung yang tercatat sejauh ini di Tiburon.
Lihat juga
[claude-managed-agents-arsitektur.md](claude-managed-agents-arsitektur.md)
— talk lain (event berbeda) tentang arsitektur & kode implementasi Claude
Managed Agents API, di mana memory + dreaming disebut sebagai salah satu
fitur "Beyond the basics".

## Evolusi arsitektur memori (4 tahap)

1. **`CLAUDE.md`** — satu file markdown, di-inject ke awal konteks tiap sesi.
2. **Memory tool** — `memory_read()`, `memory_write()`, `memory_edit()`, agent
   otonom putuskan kapan baca/tulis, in-band (dalam sesi).
3. **Skills** — memory prosedural (`SKILL.md`, frontmatter ringkas di atas +
   detail penuh di badan file) — mengatasi context bloat lewat **progressive
   disclosure**: agent baca frontmatter dulu, baru load detail kalau relevan.
4. **`memory/` sebagai file system** (state-of-the-art) — memori = sistem
   file biasa (notes/, deploy.md, team-rules.md), agent pakai tool generik
   (Bash, Grep) untuk baca/tulis, bukan tool khusus memori.

**3 pelajaran dari evolusi ini:** Format (Markdown, manusia & agent baca hal
sama) — Reading (progressive disclosure, jangan load semua sekaligus) —
Writing (agent dikasih otonomi penuh menentukan apa yang layak disimpan).

Ini **persis** cara kerja `CLAUDE.md` + `.claude/` + `docs/memory/` yang
sudah dipakai di ekosistem Shiftware/Otak — lihat
[sistem-memori-proyek.md](sistem-memori-proyek.md). Bedanya, sistem Otak baru
di tahap 1 (single file + 4-file `docs/memory/` terkurasi manual), belum di
tahap "memory tool" atau "dreaming" di bawah.

## 4 prinsip produksi (untuk memori yang dipakai banyak agent paralel/long-running)

1. **Versioning** — tiap tulisan diatribusikan ke penulis (agent/human),
   sesi, waktu; riwayat lengkap bisa di-rollback.
2. **Concurrency** — precondition content-hash sebelum tiap tulis (optimistic
   locking): ambil hash → susun draft → ambil hash lagi sebelum commit → kalau
   dua hash beda, tulisan ditolak, agent re-pull dan ulangi. Ditekankan:
   **living di harness, bukan di model** — praktik software engineering
   standar, bukan diserahkan ke penilaian model.
3. **Permissioning** — read-only untuk pengetahuan org-wide terkurasi
   (`org-conventions/`), read-write hanya untuk working memory/scratchpad
   milik agent sendiri (`team-memory/`).
4. **Portability** — API bersih di atas file biasa, memori bisa diakses
   lintas banyak product surface.

Hasil yang diklaim di produksi: 97% fewer first-pass errors, 27% lower cost,
34% lower latency (satu tim); 30% faster verification via cross-session
memory (tim lain).

## Konsep "Dreaming" — konsolidasi memori out-of-band

**Definisi:** proses batch second-order, out-of-band, asinkron, resource
sendiri — tujuan tunggal mengkurasi memori (bukan mengerjakan task user).

**Alur:** transcript sesi harian banyak agent → digabung dengan memory state
saat ini → proses Dreaming (batch periodik) analisis semua → hasilkan updated
memory state (new insights + organized structure) → sesi besok otomatis
lebih pintar.

**Arsitektur teknis satu dreaming pass:** Input memory store (`$MEM`)
di-clone jadi Output memory store (`$MEM_OUT`) → **Orchestrator** spawn satu
**Subagent per session transcript** → tiap subagent read/write ke Output
memory store untuk reorganisasi. Pola: 1 orchestrator + N subagent paralel,
tiap subagent tangani 1 transcript.

**Yang disorot subagent:** bukan cuma isi percakapan, tapi juga **tool calls
dan metadata** — paling sentral ke performa agent. Contoh pola yang bisa
kedetek: satu topik hilang total dari memori, konfigurasi tool salah
berulang, atau pola fleet-wide/org-wide yang perlu satu context change
global.

**Trade-off memory (real-time) vs dreaming (batch):** memory in-band lebih
cepat terasa efeknya tapi agent terbatas fokus & visibilitas (cuma lihat
sesi sendiri); dreaming lebih mahal (token/compute dedicated) tapi
visibilitas lebih luas (lintas sesi/lintas agent). Keduanya dirancang
**berjalan paralel**, saling melengkapi.

## Prinsip yang ditekankan

*"Do the simple thing that works"* — mulai dari `CLAUDE.md` sederhana dan
skills sebelum lompat ke sistem memori kompleks. Memory bukan cuma untuk
coding (contoh: dipakai untuk gaya penulisan slide presentasi juga).

## Klarifikasi dari sesi tanya-jawab

- "Apakah ini reinventing databases dari nol?" — jawaban presenter: sebagian
  memang sengaja kembali ke prinsip software engineering klasik (versioning,
  optimistic locking) yang terbukti bagus, dikemas ulang supaya agent otonom
  bisa berinteraksi dengannya secara efektif — bukan reinvent asal-asalan.
- Dreaming di skala enterprise dengan permission set berbeda per user — bisa
  dikonfigurasi supaya dreaming cuma menyertakan session transcript yang
  permission-nya cocok dengan target memory store.
- Solusi memory store konkret untuk enterprise → diarahkan ke produk resmi
  Anthropic: **Claude Managed Agents** (memory & dreaming API dengan
  versioning/hashing built-in).

## Cara pakai

Kandidat kuat untuk **future work** sistem memori Otak sendiri kalau volume
sesi/dokumentasi proyek makin besar: proses "dreaming" berkala (bukan cuma
update manual `docs/memory/` tiap sesi) untuk konsolidasi/pembersihan
otomatis. Belum diterapkan — ini catatan referensi arsitektur, bukan
rencana yang sudah diputuskan.
