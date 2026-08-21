# Drive C penuh — penyebabnya cache lama, bukan aplikasi baru

**Sumber:** insiden 2026-08-21 di `D:\Downloads` — drive C tinggal 13 MB
bebas. OpenClaw baru saja dipasang sehari sebelumnya dan langsung dicurigai
sebagai penyebab.

## Gejala

Drive C tinggal 13 MB bebas dari kapasitas total. Aplikasi yang baru
dipasang (OpenClaw) jadi kambing hitam pertama karena "baru saja terjadi"
terasa seperti sebab yang paling masuk akal.

## Penyebab sebenarnya

Dicek folder demi folder (`AppData\Local`, `AppData\Roaming`, home dir),
OpenClaw (`C:\openclaw`, checkout repo) cuma **513 MB** — bukan biang
keladinya. Dua penyumbang terbesar justru cache yang menumpuk **bertahun-tahun**
tanpa pernah dibersihkan:

- `AppData\Local\NVIDIA` — **19,8 GB**, cache shader (DXCache + GLCache)
- `AppData\Local\npm-cache` — **5,7 GB**, cache paket npm

Keduanya bersama membebaskan **~22 GB** kalau dibersihkan, dan keduanya
**terbentuk ulang otomatis** saat dibutuhkan — bukan file yang hilang
permanen.

## Perbaikan

1. Hapus isi `AppData\Local\NVIDIA\DXCache` dan `...\GLCache` — akan
   terbentuk ulang sendiri saat game/aplikasi jalan lagi.
2. `npm cache clean --force` — npm regenerasi cache dari registry saat
   `npm install` berikutnya.

## Cara pakai

Kalau drive C penuh mendadak, **jangan langsung menuduh aplikasi yang baru
dipasang** — ukur dulu tiap folder besar di `AppData\Local`, `AppData\Roaming`,
dan home dir (`Get-ChildItem -Recurse | Measure-Object -Sum Length` per
folder, urutkan dari terbesar). Cache shader GPU dan cache package manager
(npm, pip, dsb.) adalah kandidat pertama yang harus dicek — keduanya bisa
tumbuh puluhan GB tanpa disadari dan aman dihapus karena regeneratif. Baru
setelah itu curigai aplikasi baru kalau memang terbukti besar.
