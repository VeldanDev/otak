# Skills — indeks

Turunan dari `STANDAR.md` dan `AGENTS.md` (Slidee), dipecah per topik
supaya sesi AI tidak perlu membaca ratusan baris utuh untuk tugas yang
cuma butuh satu bagian kecil — pola "progressive disclosure" dari
[pelajaran/arsitektur-memori-agent-anthropic.md](../pelajaran/arsitektur-memori-agent-anthropic.md)
(tahap "Skills" di evolusi memori agent Anthropic).

**Baca ini dulu.** Muat berkas skill lengkap hanya kalau relevan dengan
tugas yang sedang dikerjakan.

**Kalau ada pertentangan antara skill di sini dan `STANDAR.md` /
`AGENTS.md` asli, sumber asli yang menang.** Skill ini ringkasan turunan,
bukan pengganti — kalau ada keraguan atau kasus tepi yang tidak
tercakup, buka sumber aslinya.

## Daftar skill — kapan dipakai

| Skill | Kapan dipakai |
|---|---|
| [sistem-memori](sistem-memori.md) | Proyek apa pun lintas sesi AI — wajib, tanpa kecuali |
| [arah-visual](arah-visual.md) | Proyek apa pun yang punya tampilan, sebelum baris CSS pertama |
| [tipografi](tipografi.md) | Menentukan skala heading/body/label setelah arah visual dipilih |
| [gerak](gerak.md) | Menambah animasi/transisi ke UI apa pun |
| [keamanan](keamanan.md) | Apa pun yang bisa dijangkau internet — wajib, tanpa kecuali |
| [alur-kerja](alur-kerja.md) | Sebelum menulis kode untuk fitur/perubahan apa pun |
| [hemat-token](hemat-token.md) | Produk berbasis LLM dengan volume request tinggi |
| [tooling-ai-coding](tooling-ai-coding.md) | Memilih skill/tool/prompt teknik AI, atau menimbang tool baru |
| [web-checklist](web-checklist.md) | Mengaudit/membangun situs klien UMKM |
| [seo-aeo](seo-aeo.md) | Situs/konten yang perlu ditemukan orang atau disebut AI |
| [produk-startup](produk-startup.md) | Membangun produk sendiri (bukan proyek klien) |
| [skill-ai-agent](skill-ai-agent.md) | Membangun produk berbasis LLM/AI agent |

## Berdasarkan jenis proyek

Router ini dipindah dari `STANDAR.md` Bagian 0 — tentukan dulu sedang
membangun apa, baru muat skill yang relevan:

| Sedang membangun | Muat skill | Lewati |
|---|---|---|
| **Situs statis / landing page** (Slidee, Shiftware) | sistem-memori · arah-visual · tipografi · gerak · web-checklist · seo-aeo · keamanan | hemat-token · skill-ai-agent |
| **Produk berbasis LLM** (startup AI) | Semua skill, terutama hemat-token dan skill-ai-agent | — |
| **Situs klien UMKM** (freelance) | arah-visual · tipografi · web-checklist (terutama 7 tanda + 5 kesalahan) · seo-aeo · keamanan | produk-startup (bagian YC) · skill-ai-agent |
| **Konten @veldorable** | seo-aeo (bagian AEO saja) + aturan carousel di bawah | arah-visual (web) · web-checklist · keamanan (server) |
| **Aplikasi dengan backend / banyak user** | alur-kerja (checklist scaling) · keamanan · sistem-memori | arah-visual kalau belum ada UI |
| **Belajar / riset** | skill-ai-agent · tooling-ai-coding | Sisanya sesuai kebutuhan |

**Yang selalu berlaku, apa pun yang dibangun:** sistem-memori · keamanan ·
alur-kerja (filosofi lazy senior dev) · larangan font pasaran (bagian
dari arah-visual).

## Aturan carousel @veldorable

Dipakai hanya untuk konten TikTok, tidak untuk web (detail lengkap ada
di `STANDAR.md` Bagian 0, belum dipecah jadi skill terpisah karena
singkat):

- 1080×1920, font besar
- Slide 1 selalu hook, slide terakhir selalu CTA follow @veldorable
- "swipe >>>" di tiap slide kecuali terakhir
- Tiga hashtag: #techtok #tech #veldorable
- Kalau menyebut satu tool, wajib disclaimer ada alternatif lain
- Identitas visual sendiri — meniru akun lain melawan tujuan membangun
  ciri khas

## Kalau ragu

Skill yang tidak relevan **diabaikan diam-diam**, bukan dipaksa masuk.
Skill yang dipakai di tempat yang salah lebih berbahaya daripada skill
yang tidak dipakai — terlihat seperti keputusan padahal cuma salinan.
