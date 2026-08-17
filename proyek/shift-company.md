# Identitas visual Shift Company — Koordinat (final)

Shift Company belum punya repo sendiri — baru PRD
(`D:\Downloads\PRD-SHIFT-COMPANY.md`) untuk situs perusahaan induk yang
menaungi **Slidee**, **Cords**, dan **Wagon** (lihat
[proyek/slidee.md](slidee.md), [proyek/cords.md](cords.md)). Berkas ini
salinan dari `D:\Downloads\identitas-shift-final.md` — spesifikasi
identitas visual yang sudah diputuskan, ditaruh di vault supaya tidak
tercecer di `Downloads` begitu repo `shift-company` mulai dibangun.

Riwayat lengkap tiga arah yang diusulkan (termasuk dua yang ditolak) ada
di `D:\Downloads\identitas-shift.md` — tidak disalin ke vault karena
sudah diringkas di bagian "Keputusan" di bawah.

**Status:** diputuskan 2026-08-17. Ini spesifikasi lengkap satu arah yang
dipilih dari tiga usulan di `identitas-shift.md` (Neubrutalism
"Percabangan", Minimalism sistemik "Koordinat", Glassmorphism "Lapisan").
Dokumen itu tidak dihapus — jadi rekam jejak kenapa dua arah lain
ditolak. Ini pengganti untuk implementasi, bukan pengganti riwayatnya.

**Skill yang dipakai:** `arah-visual.md`, `tipografi.md`
(`Otak/skills/INDEKS.md`). **Pola metode:** `slidee/docs/icon.md` dan
`slidee/docs/wordmark.md` — satu satuan geometris dipakai berulang di
lebih dari satu tempat, opsi yang ditolak dicatat dengan alasannya.

---

## Keputusan — dicatat supaya tidak dibongkar ulang

**Diputuskan:** Arah 2, Minimalism sistemik "Koordinat".

**Kenapa (alasan asli, bukan rekonstruksi):**

1. Minimalism sistemik terbaca sebagai **perusahaan teknik**, bukan
   studio kreatif — sesuai posisi Shift Company sebagai induk yang
   bicara ke mitra dan jurnalis, bukan konsumen produk.
2. Gagasan **koordinat** lahir dari produk sendiri — Cords memakai
   alamat (`@veldorable D3-01`) dan peta profil 4×4 sebagai konsep inti.
   Ini bukan gaya yang dipinjam dari tren luar, tapi bahasa yang sudah
   ada di dalam keluarga produk.
3. Shift Company berencana membuat **perangkat keras**. Koordinat adalah
   bahasa teknik universal, dan bentuknya (batang + celah + pergeseran)
   murni geometris — bisa dicetak dan dicap ke benda fisik. Efek kaca
   (Arah 3) tidak bisa.

**Yang ditolak, dan kenapa:**

| Arah | Kenapa ditolak |
|---|---|
| 1 — Neubrutalism "Percabangan" | Nada percaya diri cocok untuk mitra/jurnalis, tapi tidak menyampaikan "perusahaan teknik" sekuat pendekatan sistemik. Kalah timbang, bukan cacat |
| 3 — Glassmorphism "Lapisan" | **Ditolak eksplisit.** Efek kaca/blur/opasitas berlapis adalah fenomena layar — tidak ada padanannya saat dicetak atau dicap ke logam/plastik. Bertentangan langsung dengan rencana perangkat keras |

**Kalau keputusan ini mau dibongkar nanti:** jawab dulu — apakah rencana
perangkat keras berubah atau batal? Kalau tidak, alasan penolakan Arah 3
tetap berlaku apa pun tren visual saat itu, dan itu satu-satunya alasan
yang levelnya "keputusan produk", bukan "selera desain" — lebih berat
daripada dua alasan lainnya.

---

## 1. Palet

| Token | Hex | Peran |
|---|---|---|
| `kertas` | `#EFEEE6` | Latar utama |
| `kanvas` | `#DFDED2` | Latar luar / di belakang kertas |
| `permukaan` | `#F4F3EC` | Kartu terang |
| `permukaan-2` | `#E6E4D8` | Kartu alternatif |
| `tinta` | `#1C1D14` | Teks utama, latar gelap |
| `tinta-2` | `#2A2B1F` | Latar gelap sekunder |
| `abu-tua` | `#4E5047` | Teks di latar gelap |
| `abu` | `#797C6E` | Teks sekunder |
| `abu-muda` | `#94968A` | Teks tersier |
| `aksen` | `#3A5BFF` | Indigo. Penanda koordinat, bidang aktif |
| `aksen-redup` | `#E4E8FF` | Tint aksen ~10% di atas kertas — latar hover/baris terpilih, bukan bidang penuh |

Struktur token sengaja sama dengan Slidee (kertas/kanvas/permukaan ×2/
tinta ×2/abu ×3/aksen) — supaya siapa pun yang sudah paham sistem
Slidee langsung paham sistem ini. Nilai hex sengaja **tidak** identik —
kertas dan tinta di sini sedikit berbeda dari `#EDECE4`/`#16170F` milik
Slidee, cukup dekat untuk terasa sekeluarga, cukup beda untuk tidak
tertukar berdampingan.

### Aturan aksen — beda dari aturan hijau Slidee, dan kenapa

Aksen tetap dipakai hanya sebagai **bidang**, tidak pernah warna teks —
prinsip yang sama dengan hijau Slidee. Tapi arah kontrasnya **kebalikan**:

- Slidee: hijau `#C7E33B` terang → teks di atasnya pakai **tinta gelap**.
- Koordinat: indigo `#3A5BFF` jauh lebih gelap dan jenuh → teks di
  atasnya pakai **kertas terang** (atau putih), bukan tinta. Tinta gelap
  di atas indigo gagal kontras.

Ini bukan penyimpangan tanpa alasan — dicatat di sini persis supaya
tidak ada yang "memperbaiki" jadi tinta gelap karena menyamakan dengan
aturan Slidee tanpa mengecek kontras dulu.

**Maksimal satu bidang aksen indigo penuh per layar** — sama seperti
batas satu tombol hijau Slidee. `aksen-redup` boleh dipakai lebih dari
sekali (untuk highlight baris/hover), karena itu bukan bidang penuh.

---

## 2. Tipografi

**Dilarang:** Inter, Roboto, Arial, Geist, Manrope.

**Heading:** IBM Plex Mono, bobot **600**, selalu uppercase.
**Body:** Newsreader, bobot **400** (isi), **600** (penekanan inline).
Total dua bobot di seluruh sistem — tidak lebih.

Kontras yang disengaja: heading bicara seperti sistem (mono, berjarak,
huruf besar semua), body bicara seperti manusia (serif editorial). Cocok
dengan nada PRD: presisi soal fakta (status produk apa adanya), tapi
tetap manusiawi soal cerita di baliknya.

### Skala (mobile / desktop)

| Tingkat | Mobile | Desktop | Tracking | Dipakai untuk |
|---|---|---|---|---|
| H1 | 34px | 72px | +0,01em | Hero, satu-satunya di halaman |
| H2 | 24px | 38px | +0,02em | Judul section |
| H3 | 20px | 27px | +0,03em | Judul kartu — satu definisi untuk semua kartu |
| H4 | 14px | 14px | +0,04em | Sub-judul kecil di dalam blok |
| Body utama | 16px | 19px | normal | Paragraf pembuka section, line-height 1,6 |
| Body sekunder | 14px | 15px | normal | Isi kartu, teks penunjang, line-height 1,55 |

Rasio H3:body-sekunder = 27/15 = **1,8×** di desktop (di atas ambang
~1,7× dari `tipografi.md`). Di mobile 20/14 = 1,43× — sama seperti pola
nyata di skala Slidee sendiri (rasio mobile memang lebih longgar
daripada desktop di kedua sistem, bukan pelanggaran, bukan kebetulan
juga).

### Label indeks (mono, di luar tabel skala)

Dipakai untuk penomor produk (`01`, `02`, `03` di depan Slidee/Cords/
Wagon) dan angka/data teknis lain:

- Ukuran tetap **12px** (mobile dan desktop, tidak berjenjang)
- Bobot 600, tracking **+0,12em**, uppercase
- Selalu dua digit dengan nol di depan (`01` bukan `1`)

---

## 3. Bentuk khas — "Silang Koordinat"

### Rumus dasar

Kanvas abstrak **120 × 120** unit (skalakan bebas — semua angka di
bawah proporsional terhadap sisi kanvas, bukan piksel tetap).

**Tebal garis (T)** = sisi kanvas ÷ 10 = **12 unit**.

**Titik celah** diukur di **⅓ dari tepi** — satuan yang sama persis
dengan takik ikon Slidee (⅓ sisi) dan geseran wordmark (⅓ panjang
palang). Untuk bar horizontal, ⅓ diukur dari kiri (x = 40). Untuk bar
vertikal, ⅓ diukur dari atas (y = 40).

**Pergeseran** = 1×T (12 unit), diterapkan pada ruas yang lebih panjang
(⅔ sisi), searah "geser" keluarga: turun untuk bar horizontal, kanan
untuk bar vertikal — prinsip yang sama dengan palang E pada wordmark
Slidee ("satu diam, satu bergerak"), diterapkan di dua sumbu sekaligus.

### Bar horizontal (tebal 12, pusat asli y=60)

| Ruas | Rentang x | Rentang y | Catatan |
|---|---|---|---|
| Kiri (⅓, diam) | 0 → 34 | 54 → 66 | Berhenti T/2 sebelum titik celah |
| Celah | 34 → 46 | — | Lebar = T |
| Kanan (⅔, bergeser) | 46 → 120 | 66 → 78 | Turun 1×T dari posisi asli |

### Bar vertikal (tebal 12, pusat asli x=60)

| Ruas | Rentang y | Rentang x | Catatan |
|---|---|---|---|
| Atas (⅓, diam) | 0 → 34 | 54 → 66 | Berhenti T/2 sebelum titik celah |
| Celah | 34 → 46 | — | Lebar = T |
| Bawah (⅔, bergeser) | 46 → 120 | 66 → 78 | Bergeser kanan 1×T dari posisi asli |

**Titik silang:** ruas kanan bar horizontal (x 46–120, y 66–78) dan ruas
bawah bar vertikal (y 46–120, x 66–78) bertemu tepat di kotak **x 66–78,
y 66–78** (12×12, persis T×T). Ini satu-satunya titik potong — dan
sengaja **tidak** di pusat kanvas (60,60), melainkan digeser ke (72,72).
Ruas "diam" (kiri dan atas) berhenti jauh sebelum pusat, jadi yang
membentuk silang justru dua ruas yang sudah bergeser. Mark ini bukan
tanda tambah netral — ia adalah koordinat yang sudah dipindah, dengan
sisa posisi lama masih terlihat sebagai dua potongan pendek di tepi.

**Ruang aman:** clearance minimal 12% sisi kanvas (≈14 unit pada kanvas
120) di sekeliling mark saat ditaruh berdampingan elemen lain — angka
yang sama dengan konvensi ruang aman ikon Slidee (11% sisi, dibulatkan
ke atas di sini karena mark ini punya dua bar penuh-sisi, bukan satu
cangkang tertutup).

### Varian ukuran kecil

Di bawah ~24 unit pada layar (setara ikon 16–24px atau grafir < 8mm),
celah selebar T mudah menyatu karena bleed rendering/laser. **Varian
kecil:** lebar celah dilebarkan jadi 1,5×T, dan pergeseran perpendikular
**dihapus** (kedua bar jadi silang simetris biasa, tanpa langkah) — pola
yang sama dengan penyesuaian radius ikon Slidee di 16px (112→72):
proporsi utama tetap, detail halus disederhanakan supaya tetap terbaca
di ukuran kecil.

---

## 4. Aturan penggunaan

**Boleh:**
- Menskalakan utuh — rasio ⅓, T, dan pergeseran 1×T tetap proporsional
  terhadap sisi kanvas berapa pun ukurannya
- Menukar tinta/kertas sesuai latar (satu geometri, dua nada — pola yang
  sama dengan "Jalan A" ikon Slidee)
- Mencetak sebagai satu warna solid untuk kebutuhan cetak, grafir, atau
  perangkat keras
- Memakai berulang sebagai penomor kecil (mis. di depan tiap baris
  produk), bukan cuma sebagai satu mark besar tunggal

**Jangan:**
- Mengubah titik celah dari ⅓ atau besar pergeseran dari 1×T
- Membuat celah lebih sempit dari T — dua ruas yang menyatu kembali
  menghilangkan pembacaan "koordinat yang bergeser", jadi silang biasa
  tanpa arti
- Menambahkan blur, gradien, bayangan, atau efek kaca — itu ciri Arah 3
  yang sudah ditolak, secara sengaja tidak ada di sini
- Memutar mark
- Mencetak aksen indigo langsung ke material logam/plastik tanpa proses
  warna tersedia (lihat § 5) — pakai versi monokrom
- Memakai mark ini sebagai pengganti huruf pertama pada wordmark, kalau
  nanti wordmark Shift Company dibuat terpisah

---

## 5. Catatan khusus untuk perangkat keras

Ini alasan utama Arah 2 dipilih, jadi aturan di bagian ini bukan
tambahan opsional — ini yang membuat identitasnya valid untuk dicetak
ke benda fisik.

**Wajib ada versi monokrom.** Mark harus tetap terbaca penuh sebagai
siluet satu warna — tanpa opasitas, gradien, atau bidang kedua. Dua
bar + celah + pergeseran cukup jadi bentuk itu sendiri, tidak butuh
warna untuk dibaca.

- **Di material terang** (aluminium anodized terang, plastik putih):
  cetak/grafir dengan `tinta` (`#1C1D14`) solid.
- **Di material gelap** (logam gelap, plastik hitam): cetak/emboss
  dengan `kertas` (`#EFEEE6`) solid, atau biarkan tanpa warna
  (cukup relief/grafir tanpa isi warna) kalau prosesnya emboss/etsa.
- **Indigo (`aksen`) tidak dipakai di hardware** kecuali proses
  produksinya memang mendukung warna (cat, decal, soldermask PCB).
  Default hardware selalu monokrom.

**Ukuran garis minimum** — verifikasi ke vendor fabrikasi sebelum kirim
file produksi, tapi sebagai titik awal:
- Grafir laser (logam/plastik): T tidak boleh render di bawah **0,6mm**
- Stempel/emboss/tekan (cetak timbul): T minimal **1mm** — proses ini
  butuh garis lebih tebal daripada grafir supaya cetakannya tidak pecah
- Sablon/soldermask (PCB, label): T minimal **0,3mm**, tapi cek toleransi
  proses pabrik spesifik

**Berkas terpisah untuk hardware:** pakai varian ukuran kecil (§ 3, gap
1,5×T tanpa pergeseran) sebagai master grafir kalau mark akan dicap di
bawah ~15mm fisik — jangan pakai geometri penuh (dengan pergeseran) di
ukuran fisik kecil, detailnya akan hilang di material nyata sama seperti
di layar kecil.

---

## Ringkasan satu halaman

| | Nilai |
|---|---|
| Gaya | Minimalism sistemik |
| Kertas / Tinta | `#EFEEE6` / `#1C1D14` |
| Aksen | `#3A5BFF` (indigo), bidang saja, teks di atasnya pakai kertas |
| Heading | IBM Plex Mono 600, uppercase |
| Body | Newsreader 400 (isi) / 600 (tekanan) |
| Bentuk khas | Silang Koordinat — dua bar, celah di ⅓, pergeseran 1×T |
| Hardware | Selalu ada versi monokrom; indigo tidak dicetak ke logam tanpa proses warna |
