# Riset — pointer, bukan salinan

Repo asli: `D:\vscode\MyProjects\Riset\`. Isinya **tidak disalin** ke sini —
kalau butuh isi analisisnya, buka repo itu langsung atau cari lewat
`tiburon.py`.

## Isi repo Riset

- `analisis-buku.md` — ringkasan 8-baris per buku teknis (folder topik,
  jumlah halaman, penulis, topik, konsep utama, bisa dipakai untuk apa)
- `analisis-buku-dalam.md` — analisis mendalam per buku (daftar isi per bab,
  ringkasan tiap bab, istilah teknis, contoh kode) untuk buku yang butuh
  detail lebih dari ringkasan 8-baris
- `analisis-video.md` — analisis video/carousel TikTok edukasi (topik,
  narasi, isi layar, poin praktis), sebagian besar dari akun `@veldorable`
  milik pembuat Slidee/Cords
- `scan-konten.py` — pemindai `D:\Downloads` untuk berkas media baru
  (`.mp4 .mov .jpg .jpeg .png`), hash MD5 dicocokkan ke `.konten-index.json`
  supaya tidak dianalisis ulang. **Dirancang jalan dari `D:\Downloads`**,
  bukan dari `Riset/` — jalankan salinan aslinya di Downloads untuk
  pemindaian baru.
- `tiburon.py` — pencarian kata kunci lintas ketiga berkas markdown di atas

## Cara mencari — tiburon.py

```
python tiburon.py "kata kunci"          # cuplikan tiap entri yang cocok
python tiburon.py "kata kunci" --full   # entri lengkap
python tiburon.py                       # daftar semua judul yang ada
```

Python bawaan saja, tidak ada dependency pihak ketiga. Sumber pencarian:
`analisis-buku.md`, `analisis-buku-dalam.md`, `analisis-video.md`.

## Sumber asli: proyek Tiburon di Downloads

Dikonfirmasi 2026-08-16: `D:\Downloads\Tiburon\` adalah proyek aslinya,
dengan struktur `03-hasil-analisis/` berisi `analisis-buku.md`,
`analisis-buku-dalam.md`, `analisis-video.md`, `.konten-index.json`, dan
`.pdf-text-cache/` — **jauh lebih lengkap dan lebih baru** daripada salinan
di `Riset/` (mis. `analisis-buku-dalam.md` ~577 KB di Tiburon vs versi lebih
kecil di `Riset/`). `Riset/` tampaknya salinan lama yang diratakan
(markdown-nya langsung di root, bukan di subfolder) dan tidak selalu
disinkronkan dengan yang di Downloads. **Untuk riset paling lengkap dan
terbaru, cek `D:\Downloads\Tiburon\` dulu, bukan `Riset/`.**

## Bug path — sudah diperbaiki 2026-08-16

`tiburon.py` sebelumnya hanya membaca dari
`BASE_DIR / "03-hasil-analisis" / <namaberkas>` — cocok untuk struktur
`Tiburon/` asli, tapi gagal total di `Riset/` karena ketiga markdown ada
langsung di root sana, bukan di subfolder.

Perbaikannya: `tiburon.py` sekarang mengecek **root dulu, baru
`03-hasil-analisis/`** untuk tiap berkas (lihat `SOURCE_DIRS` di kepala
skrip). Diperbaiki di sumber asli `D:\Downloads\Tiburon\tiburon.py`, lalu
disalin ke `Riset/tiburon.py`. Dites jalan di kedua lokasi (336 entri
ditemukan di keduanya).

## Cara pakai

`tiburon.py` sekarang jalan baik dari `Riset/` maupun dari
`D:\Downloads\Tiburon\`. Kalau butuh analisis paling lengkap/terbaru, jalankan
dari `D:\Downloads\Tiburon\` (lihat catatan di atas).
