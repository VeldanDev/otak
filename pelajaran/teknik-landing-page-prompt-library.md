# Landing page animasi premium dari prompt library + Claude Code

**Sumber:** `D:\Downloads\Tiburon\03-hasil-analisis\analisis-video.md`, entri
video `tutorwebprem2.mp4` (talking-head 36 detik). **Counterpart** dari
[teknik-hero-scroll-3d.md](teknik-hero-scroll-3d.md) — sama-sama "bikin situs
animasi premium tanpa coding manual", tapi jalur beda: di sini prompt-nya
sudah jadi (tinggal copy), Claude Code yang generate seluruh situs dari teks,
bukan cuma satu komponen scroll dari foto produk.

## Resep (5 langkah)

1. **Kunjungi situs prompt library** — galeri/marketplace berisi kartu
   preview desain hero-section animasi, berlabel kategori & status
   (Premium/Copy). Banner yang terbaca di video: **"motionsites"**
   ("Animated backgrounds designed to convert, impress, and amaze") —
   *nama situs tidak dieja lengkap sebagai URL di video maupun teks layar*,
   cuma banner itu yang terlihat, jadi anggap ini petunjuk nama, bukan URL
   terkonfirmasi.
2. **Pilih desain yang disuka, copy prompt-nya** — sebagian kartu berbayar
   (Premium), sebagian gratis (tombol "Copy" langsung).
3. **Buka Claude Code, paste prompt itu persis.**
4. **Tambahkan deskripsi brand sendiri** — habis paste prompt template,
   jelaskan brand-nya tentang apa supaya hasil generate disesuaikan
   (bukan generik).
5. **Generate → tweak → deploy gratis** — Claude generate situs 3D animasi
   lengkap (smooth animations, clean layout, sleek UI), lalu disesuaikan
   manual sampai cocok brand style, deploy pakai **Vercel** atau **Netlify**.

## Pola desain yang konsisten di semua contoh yang ditunjukkan

1 hero visual dominan (animasi/3D/foto besar) + headline pendek bold + 1 CTA
jelas. Situs contoh yang dipakai sebagai demo di video: Asme ("Built for the
curious" — SaaS gelap, partikel orbit biru), situs perhiasan "Reveal in
Radiance", Ford "Rediscover the Classics", motor custom "Lean Into It",
poster film "No Way Home", produk perekam musik "Loop".

## Cara pakai

Cocok untuk MVP/demo cepat yang butuh landing page bertema hero-animasi —
**bukan pengganti desain custom** untuk produk utama, karena hasilnya
template-driven (prompt sudah jadi, disesuaikan seadanya lewat deskripsi
brand). Kalau butuh referensi cepat sumber prompt untuk brief klien agency
atau eksperimen landing page produk sendiri, ini jalur tercepatnya — tapi
jangan dipakai sebagai identitas visual final tanpa disesuaikan lebih jauh.
