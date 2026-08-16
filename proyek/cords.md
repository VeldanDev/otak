# Cords

Sumber: `Cords/docs/memory/{README,STATUS,decisions,progress}.md`,
`Cords/AGENTS.md`. Update terakhir sumber: 2026-08-09 (STATUS.md tertanggal
2026-08-08, tapi `decisions.md` punya entri D-098 bertanggal 9 Agustus 2026 —
lebih baru dari STATUS.md, jadi STATUS.md kemungkinan sudah agak basi).

## Apa

Aplikasi sosial mobile web. Nama dari **Record + Coordinates** — harfiah:
tiap konten punya alamat koordinat. **Cords adalah bidang dua dimensi tak
terbatas, bukan feed** — pengguna bergerak ke segala arah untuk menjelajah.
Menggabungkan lima format konten (video, foto, teks, berita, story) yang di
platform lain terpisah-pisah.

Tiga lapis koordinat direncanakan: peta global (v1, posisi dari hash), Profile
Coordinates (v1, disusun manual oleh kreator), Cords reference lintas kreator
(v2, butuh data pengguna nyata).

Untuk siapa (v1): penonton `@veldorable`, channel TikTok edukasi teknologi
milik pembuatnya sendiri — bukan pengguna asing dari nol. Ini keputusan
sadar untuk menghindari pola gagal Slidee (lihat
[../pelajaran/jangan-poles-sebelum-pengguna.md](../pelajaran/jangan-poles-sebelum-pengguna.md)).

Produk di bawah Shift Company, sama seperti Slidee.

## Stack

Next.js · React · TypeScript · Tailwind. Supabase (Auth + Postgres + RLS +
Realtime) untuk backend (D-020). Media: Supabase Storage untuk v1, rencana
pindah ke Cloudflare Stream kalau bandwidth-nya habis (D-037, mengoreksi
keputusan awal D-021). Pencarian pakai Postgres full-text (`tsvector` + GIN),
bukan mesin terpisah (D-022). Ada juga percobaan build APK lewat Capacitor
(`capacitor.config.ts` ada di root repo).

Repo privat: `github.com/VeldanDev/cords`. Live di `cords-mu.vercel.app`
(Vercel Hobby — **hanya untuk non-komersial**, wajib naik paket begitu Cords
menghasilkan uang, D-032).

## Status (per sumber terbaru yang tercatat, 2026-08-09)

Fase prototipe (7 putaran, teruji jempol di HP) sudah **selesai dan ditutup
secara sadar** — lihat `STATUS.md`: "Fase prototipe: SELESAI. Jangan
diteruskan." Arsitektur terkunci: bidang tak terbatas, dua tab beranda
(Jelajah + For Your Coordinates), Profile Coordinates milik kreator, lima
format konten, minat tanpa skor.

Aplikasi tersambung Supabase, konten pertama sudah tersimpan (2026-08-08).
Auth email (magic link) dan Google jalan di web. Login Google **di dalam
APK dihentikan** (D-098, 2026-08-09) — jalur deep link terbukti buntu karena
Chrome Custom Tab menolak mengikuti redirect ke skema non-http. Penggantinya
(Google Sign-In native + `signInWithIdToken`) sudah dirancang tapi **belum
dikerjakan** — prasyaratnya (plugin native, OAuth client Android, SHA-1
keystore yang dipatok) di luar kode. Email+password sudah jalan di APK dan
dipakai untuk sekarang.

## Syarat rilis — jangan dilewati

Ganti pengiriman email dari SMTP bawaan Supabase (dibatasi ketat, gampang
kena rate limit) sebelum rilis ke penonton TikTok. Dua opsi: SMTP sendiri
lewat Resend, atau login Google (native, bukan deep link — lihat D-098).
Sebaiknya keduanya.

## Utang teknis yang sengaja ditinggalkan

Kotak jejak debug di layar masuk (`.mkJejak`, kunci localStorage
`cords.jejak`) sengaja dibuat jelek supaya tidak lupa dicabut sebelum APK
dibagikan ke siapa pun di luar pemilik.

## Langkah berikutnya

Per `STATUS.md` (2026-08-08, mungkin sudah agak basi — lihat D-098 yang lebih
baru): sambungkan unggah media ke penyimpanan, isi 20 konten `@veldorable`,
lalu rilis ke penonton TikTok. Cek `docs/memory/STATUS.md` di repo Cords
sendiri untuk keadaan paling akurat.

## Pertanyaan terbuka (belum diputuskan per sumber ini)

- Nama "Cords" berisiko — satu huruf dari Discord, kategori sama
- Warna ungu `#8A2BE6` sudah diuji baik di HP tapi belum final
- Apakah Wagon (produk Shiftware lain) akan berbagi satu proyek Supabase
  dengan Cords — harus diputuskan sebelum Wagon mulai dibangun (D-082)
