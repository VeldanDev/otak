# Arah visual

**Sumber:** `STANDAR.md` Bagian 2. Contoh penerapan nyata:
`Website/slidee/AGENTS.md` § 7 (identitas visual final Slidee).

## Kapan dipakai

Apa pun yang punya tampilan — web, aplikasi, slide, dokumen. Satu dari
empat aturan yang selalu berlaku apa pun yang dibangun (kecuali murni
backend).

## Lewati kalau

Murni backend tanpa UI, atau arah visual proyek ini **sudah diputuskan
dan final** (mis. Slidee — jangan tarik ke arah lain).

## Input

- Siapa target user, karakter brand yang diinginkan
- Apakah proyek sudah punya arah visual final di `AGENTS.md`

## Langkah

1. **Pilih satu** dari lima arah visual sebelum baris CSS pertama:

   | Arah | Ciri | Cocok untuk | Awas |
   |---|---|---|---|
   | Glassmorphism | layer transparan, blur, border tipis | dashboard, overlay | kontras teks mudah jatuh |
   | Neubrutalism | border tebal, bayangan keras, warna mencolok | brand muda, portfolio | mudah jadi ramai |
   | Skeuomorphism | tekstur, bevel, bayangan fisik | aplikasi audio, alat kontrol | berat, kurang fleksibel |
   | Minimalism | ruang kosong lega, palet terbatas | hampir semua produk | hambar tanpa hierarki + satu aksen kuat |
   | Claymorphism | sudut sangat bulat, soft 3D, pastel | edukasi anak, onboarding | elemen besar makan ruang |

2. Tulis pilihan di `AGENTS.md` proyek sebelum menulis kode.
3. **Font dilarang:** Inter, Roboto, Arial, Geist, Manrope — netral tanpa
   karakter, jadi penanda "dibuat AI tanpa keputusan". Detail skala →
   [tipografi.md](tipografi.md).
4. Tiga hal yang bikin produk terlihat profesional (bukan soal
   kerumitan): desain bersih & konsisten, bahasa jelas, struktur
   terorganisir.
5. (Opsional, proyek baru tanpa arah) alur Stitch: kumpulkan referensi →
   `design.md` + prompt Stitch → stitch.withgoogle.com → pilih varian →
   serahkan ke Claude untuk diimplementasikan.

## Contoh

Slidee: **Minimalism** + satu aksen hijau (`#C7E33B`, hanya sebagai
bidang, maksimal satu tombol hijau per layar, tidak pernah warna teks) +
bentuk khas "Geser" (satu benda, satu pergeseran sepertiga,
`clip-path: polygon(0 0, 84% 0, 100% 12%, 100% 100%, 0 100%)`).

## Format keluaran

Entri `AGENTS.md` § arah visual: nama arah dipilih + alasan singkat +
daftar warna/token + font heading/body + font yang dilarang.
