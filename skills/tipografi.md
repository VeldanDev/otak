# Tipografi

**Sumber:** `STANDAR.md` Bagian 2 (§ Font). Contoh skala lengkap:
`Website/slidee/AGENTS.md` § 7 (§ Tipografi).

## Kapan dipakai

Menentukan atau meninjau skala teks (heading, body, label) untuk produk
yang **arah visualnya sudah dipilih** — lihat [arah-visual.md](arah-visual.md)
dulu kalau belum.

## Input

- Arah visual yang sudah dipilih
- Daftar level teks yang dibutuhkan (H1–H4, body utama/sekunder, label/mono)

## Langkah

1. **Dilarang** Inter, Roboto, Arial, Geist, Manrope. Pilih font yang
   punya sikap, lalu konsisten.
2. Buat skala berjenjang mobile/desktop — tiap tingkat beda **≥2px** dari
   tetangganya supaya kelihatan mata. Jangan bikin varian setengah piksel
   (16,5 vs 17 vs 17,5) untuk elemen yang perannya sama.
3. Jaga rasio heading:body di atas **~1,7x** di semua tingkat — di bawah
   itu, heading dan body terasa nyaris sama besar (kegagalan nyata yang
   pernah terjadi di FAQ Slidee sebelum diperbaiki).
4. Batasi bobot font ke 1–2 nilai (mis. hanya 500 dan 600) — jangan biarkan
   tiap komponen memilih bobotnya sendiri.
5. Satu definisi per peran (mis. H3 = judul kartu) dipakai di semua
   tempat yang perannya sama — jangan bikin varian baru per komponen.
6. Kalau ada teks mono/label/angka, pakai secara sungguhan (timecode,
   rasio, hitungan) — bukan dekorasi kosong.

## Contoh

Skala Slidee (mobile / desktop):

| Tingkat | Mobile | Desktop | Tracking | Dipakai untuk |
|---|---|---|---|---|
| H1 | 36px | 88px | −0,035em | Hero, satu-satunya di halaman |
| H2 | 28px | 46px | −0,025em | Judul section |
| H3 | 21px | 26px | −0,02em | Judul kartu (satu definisi semua kartu) |
| H4 | 16px | 16px | −0,015em | Sub-judul kecil |
| Body utama | 16px | 18px | normal | Paragraf pembuka section |
| Body sekunder | 14px | 15px | normal | Isi kartu, jawaban FAQ |

Font: Instrument Sans 600 (heading), IBM Plex Sans 400 (body), IBM Plex
Mono 500 (angka/label, uppercase, tracking +0,1–0,14em).

## Format keluaran

Tabel skala tipografi (tingkat × ukuran mobile/desktop × tracking ×
dipakai untuk) siap tempel ke `AGENTS.md`, plus daftar font per peran.
