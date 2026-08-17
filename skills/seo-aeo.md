# SEO & AEO

**Sumber:** `STANDAR.md` Bagian 6.

## Kapan dipakai

Apa pun yang perlu ditemukan orang — situs dan konten. Berlaku juga
untuk konten @veldorable (ambil bagian AEO saja, bukan arah visual web).

## Input

- Domain/URL, dan apakah sudah terdaftar di Google Search Console

## Langkah

1. Hindari enam kesalahan SEO pemula: tidak menguasai dasar, menargetkan
   keyword terlalu sulit (pakai **long-tail 3–5 kata** — persaingan
   lebih kecil, hasil lebih cepat), tidak mengukur hasil, berharap hasil
   instan (butuh 2 minggu–3 bulan, konsisten bukan buru-buru), terlalu
   bergantung AI tanpa sentuhan manusia (manusia menang ~80% dibanding
   full-AI), tidak membangun portofolio sendiri.
2. Sitemap & GSC, dua langkah sekali jalan (~10 menit), tanpa ini kerja
   SEO lain sia-sia:
   - Buat `app/sitemap.ts` + `app/robots.ts` (Next.js App Router)
   - Verifikasi domain di Google Search Console, kirim URL sitemap
3. AEO — yang dikejar bukan cuma ranking, tapi apakah brand **disebut**
   ChatGPT/Claude saat orang bertanya. Yang membuatnya muncul: info
   bisnis konsisten di banyak tempat (situs, Google Business, direktori),
   halaman menyebut lokasi/layanan eksplisit, struktur mudah dibaca
   mesin.
4. Sebelum berharap muncul di jawaban AI: skor PageSpeed mendekati
   hijau semua (Performa, Aksesibilitas, Praktik Terbaik, SEO). Cek juga
   skor "Penjelajahan Agentik" kalau tersedia — standar Google soal
   kesiapan situs dibaca AI/agent, beda dari SEO tradisional.
5. Verifikasi manual: tanya langsung ke ChatGPT dengan kata kunci
   relevan, lihat apakah situs disebut. Tidak ada jaminan, hanya bisa
   diupayakan.

## Contoh

Kasus rental alat proyek Berau: PageSpeed 100/96/100/100, biaya perbaikan
~Rp3 juta, hasil jadi rekomendasi pertama jawaban ChatGPT.

## Format keluaran

Checklist: `app/sitemap.ts` + `app/robots.ts` ada → didaftarkan di GSC →
skor PageSpeed 4 kategori → hasil tes manual "disebut AI atau tidak".
