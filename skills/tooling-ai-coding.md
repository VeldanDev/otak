# Tooling & prompt teknik AI coding

**Sumber:** `STANDAR.md` Bagian 3 (§ Ekosistem skill, § Perintah Claude,
§ Tiga teknik prompt) dan Bagian 9 (§ Yang ditolak).

## Kapan dipakai

Memilih skill/tool/prompt teknik untuk mempercepat kerja dibantu AI —
saat mulai proyek baru atau menemukan hasil AI terasa generik/lambat.

## Input

- Masalah spesifik yang mau diselesaikan (desain generik? butuh
  keputusan cepat dengan banyak variabel? butuh review sebelum launch?)

## Langkah

1. Skill desain (lewat `npx skills add ...`): frontend-design (paksa
   pilih arah visual, blokir font pasaran), web-accessibility, web-design-
   guidelines. **Ambil lapisan UX ui-ux-pro-max, tolak saran visualnya**
   — pernah menyarankan Neo Brutalism + pink/biru + Inter, lebih generik
   dari arah yang sudah dipilih sendiri.
2. Perintah Claude jarang dipakai, dan kapan pakai:

   | Perintah | Kapan |
   |---|---|
   | `/ultrathink` | Masalah dengan banyak variabel |
   | `/premortem` | Sebelum komit besar |
   | `/tripwire` | Keputusan dengan banyak variabel bergerak |
   | `/redteam` | Sebelum launch |
   | `/ghost` | Sebelum kirim cold email/copy publik |

3. Teknik prompt:
   - **Ask clarifying questions** — minta AI tanya 3 hal dulu sebelum
     jawab, mencegah tebak-tebakan di asumsi awal.
   - **Artifacts** — minta hasil sebagai aplikasi interaktif, bukan
     penjelasan.
   - **OODA** — awali dengan "OODA:" untuk keputusan bervariabel banyak
     dan datanya masih asumsi.
4. **Sebelum pasang tool baru, tanya:** masalah apa yang dia selesaikan,
   dan apakah proyek ini punya masalah itu. Tool yang muncul di daftar
   "wajib 2026" tidak otomatis berlaku.

## Contoh

Ditolak dan alasannya (jangan ulangi tanpa alasan baru):

| Tool | Alasan ditolak |
|---|---|
| Aider, Cline, OpenHands | Tumpang tindih penuh dengan Claude Code |
| qrouter | Berguna untuk produk LLM, tidak untuk situs statis |
| Saran visual ui-ux-pro-max | Lebih generik daripada arah yang sudah dipilih |
| Gaya visual carousel orang lain | Meniru identitas orang lain |

## Format keluaran

Satu baris keputusan per tool baru: nama tool → masalah yang
diselesaikan → dipakai/ditolak → alasan (catat di `decisions.md`
proyek, lihat [sistem-memori.md](sistem-memori.md)).
