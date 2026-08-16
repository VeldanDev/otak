# Deploy Vercel diam-diam gagal karena email git tak terverifikasi

**Sumber:** muncul di dua proyek terpisah — `Website/slidee/docs/memory/progress.md`
(2026-08-07) dan `Cords/docs/memory/decisions.md` D-036 (2026-08-08). Karena
berulang di dua repo berbeda, ini pola nyata, bukan kebetulan sekali.

## Gejala (menipu)

Deployment Vercel berstatus **Blocked**, bukan **Failed**. Build tidak pernah
jalan, tidak ada log, situs diam-diam tetap menyajikan versi lama. Tidak ada
satu pun tanda di pesan error yang menunjuk ke penyebab sebenarnya.

Versi Cords (D-036) menambahkan detail: dialog Redeploy sempat menampilkan
*"Hobby teams do not support collaboration. Please upgrade to Pro"* dengan
tombol Upgrade — ini **menyesatkan**, bukan masalah paket. Trial Pro tidak
memperbaikinya.

## Penyebab

Email di `git config user.email` (di Cords: `yasurtraadityasuryaputra09@gmail.com`)
tidak terdaftar/terverifikasi di akun GitHub yang dipakai push. Vercel
menolak membangun commit yang identitas penulisnya tidak bisa dipastikan.

## Perbaikan

1. Tambahkan email itu di `https://github.com/settings/emails`, verifikasi
   lewat tautan yang dikirim.
2. Push commit **baru** — `git commit --allow-empty` sudah cukup.
   Deployment yang sudah terlanjur Blocked **tidak bisa dihidupkan ulang**;
   Vercel sendiri menjawab "Please try again from a fresh commit."

## Cara pakai

Kalau deploy Vercel macet lama tanpa build log atau error yang jelas, cek
`git config user.email` dan status verifikasinya di GitHub **sebelum**
menyalahkan paket, quota, atau konfigurasi lain. Kalau sempat mengaktifkan
trial Pro untuk debug ini (seperti di Cords), ingat turunkan lagi ke Hobby
sebelum trial berakhir — proyek yang belum menghasilkan uang tidak
membutuhkan $20/bulan.
