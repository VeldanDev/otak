# Otak — Indeks

Basis pengetahuan gabungan lintas repo di `D:\vscode\MyProjects`. Baca berkas
ini dulu di tiap sesi AI baru — jangan baca ulang seluruh repo dari nol.

Disusun 2026-08-16 dari sumber yang ada saat itu. Kalau sebuah proyek sudah
banyak berubah sejak tanggal update terakhirnya (lihat kolom Update), percayai
`docs/memory/STATUS.md` proyek itu sendiri, bukan ringkasan di sini.

## Proyek

| Proyek | Apa | Status singkat | Update terakhir | Baca lanjut |
|---|---|---|---|---|
| **Slidee** | Landing page pra-rilis untuk alat penjadwalan konten multi-platform | Live, waitlist jalan, belum ada pendaftar | 2026-08-16 | [proyek/slidee.md](proyek/slidee.md) |
| **Cords** | Aplikasi sosial mobile web — "bidang" konten berkoordinat, bukan feed | Live di web + APK percobaan, backend jalan, belum dirilis ke penonton | 2026-08-09 | [proyek/cords.md](proyek/cords.md) |

Keduanya produk di bawah **Shift Company**. Slidee adalah percobaan pertama;
Cords percobaan kedua yang sengaja mengoreksi pola gagal Slidee (lihat
[pelajaran/jangan-poles-sebelum-pengguna.md](pelajaran/jangan-poles-sebelum-pengguna.md)).

## Aturan lintas proyek

`STANDAR.md` — aturan kerja lintas repo (sistem memori, arah visual, keamanan,
filosofi lazy senior dev, checklist launch). Sumber: 121 gambar + 51 video
diringkas jadi aturan pakai.

Salinan ada di `Website/slidee/STANDAR.md` dan (sejak 2026-08-16, disalin
untuk menutup gap yang ditemukan) `Cords/STANDAR.md`.

Baca **Bagian 0 (Router)** dulu di `STANDAR.md` — dokumen itu berisi aturan
untuk beberapa jenis pekerjaan berbeda, tidak semua berlaku sekaligus.

## Pelajaran lintas proyek

Bug yang sudah dipecahkan, jebakan teknis, dan keputusan yang tidak boleh
diulang. Lihat isi tiap berkas untuk detail dan sumbernya:

- [pelajaran/sistem-memori-proyek.md](pelajaran/sistem-memori-proyek.md) — kenapa `docs/memory/` ada, dan aturan kerasnya
- [pelajaran/jangan-poles-sebelum-pengguna.md](pelajaran/jangan-poles-sebelum-pengguna.md) — pola gagal Slidee, dikoreksi sengaja di Cords
- [pelajaran/deploy-vercel-email-git.md](pelajaran/deploy-vercel-email-git.md) — deploy Vercel diam-diam Blocked, muncul di Slidee dan Cords
- [pelajaran/privasi-di-lapisan-data.md](pelajaran/privasi-di-lapisan-data.md) — janji privasi harus ditegakkan di server, bukan cuma UI
- [pelajaran/typecheck-tidak-jaminan-build.md](pelajaran/typecheck-tidak-jaminan-build.md) — jebakan Next.js App Router (Suspense, wrapper CSS)
- [pelajaran/tailwind-v4.md](pelajaran/tailwind-v4.md) — Tailwind v4 beda dari v3, data latih AI sering salah

- [pelajaran/setup-mcp-obsidian.md](pelajaran/setup-mcp-obsidian.md) — cara memasang MCP Obsidian (`obsidian-mcp-server` + plugin Local REST API) yang terbukti jalan, dan jebakan alamat/TLS/paket salah
- [pelajaran/teknik-hero-scroll-3d.md](pelajaran/teknik-hero-scroll-3d.md) — resep hero produk scroll-3D murah (foto → Google Flow → EZGIF ke JPG sequence 30fps → AI coding agent render per-scroll), dikonfirmasi 2 sumber video independen
- [pelajaran/teknik-landing-page-prompt-library.md](pelajaran/teknik-landing-page-prompt-library.md) — bikin landing page animasi dari prompt library ("motionsites") + Claude Code, deploy Vercel/Netlify — jalur lain menuju hasil serupa scroll-3D
- [pelajaran/arsitektur-memori-agent-anthropic.md](pelajaran/arsitektur-memori-agent-anthropic.md) — talk Anthropic soal evolusi memori agent (CLAUDE.md → memory tool → skills → memory/) + konsep "dreaming" (konsolidasi out-of-band), relevan untuk future work sistem memori Otak sendiri
- [pelajaran/claude-managed-agents-arsitektur.md](pelajaran/claude-managed-agents-arsitektur.md) — arsitektur + 7 fungsi kode Python untuk bangun agent di atas Claude Managed Agents API (agent/environment/session, event streaming, local tool handler) — referensi implementasi langsung-pakai dari workshop resmi Anthropic

## Riset

`Riset/` — arsip analisis buku teknis dan konten TikTok edukasi, dicari lewat
`tiburon.py`. **Bukan disalin ke sini** — lihat
[riset/index.md](riset/index.md) untuk cara pakai. Sumber aslinya
`D:\Downloads\Tiburon\`, bukan `Riset/`.

## Yang belum tercakup di sini

Folder lain di `D:\vscode\MyProjects` (`AI`, `C#`, `Cysec`, `Laravel`,
`Mobile`, `Next.js`, `Portofolio`, `Tools Random`, `UptimeGuard`, `Vibecode`,
`agenttrace`, dan sub-proyek `Website/` lain: `angkringan-sedulur`,
`hl-internal-finance`, `prime-property`) **belum punya sistem memori**
(`docs/memory/`) — tidak ada sumber untuk diringkas jujur, jadi sengaja
dilewati. `Website/shift-drives` diarsipkan (repo lama Slidee sebelum rename,
lihat `slidee/AGENTS.md` § 1).

Kalau salah satu proyek itu mulai aktif dikerjakan, buat `docs/memory/`
di repo-nya dulu (lihat STANDAR.md Bagian 1), baru tambahkan entrinya di sini.

`Website/AGENTS.md` (root) berisi aturan lama "Shiftware" dari sebelum
rename ke Slidee dan sebelum situsnya dipindah ke `Website/slidee/`. Sudah
diberi catatan usang di atasnya (2026-08-16) yang menunjuk ke
`Website/slidee/AGENTS.md` — tidak berlaku untuk `prime-property`,
`hl-internal-finance`, atau `angkringan-sedulur`, meski secara hierarki
letaknya di atas ketiganya.
