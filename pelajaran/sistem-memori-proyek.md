# Sistem memori proyek berbasis berkas

**Sumber:** `STANDAR.md` Bagian 1, diterapkan nyata di `Website/slidee/docs/memory/`
dan `Cords/docs/memory/`.

## Aturan

Tiap proyek yang dikerjakan lintas sesi AI butuh empat berkas di
`docs/memory/`:

- `README.md` — apa proyek ini, untuk siapa, di mana dipublikasikan, kenapa
  penting, **apa hambatan sebenarnya** (biasanya bukan yang kelihatan dulu)
- `STATUS.md` — sudah selesai apa, sedang dikerjakan apa, **satu** langkah
  berikutnya, blocker, pertanyaan terbuka
- `progress.md` — catatan kerja per sesi, terbaru di atas. Format:
  Dikerjakan / Diubah / Dicoba / **Tidak berhasil** / Dipelajari / Berikutnya
- `decisions.md` — satu keputusan per entri: apa yang diputuskan, kenapa, apa
  yang ditolak

Bagian **"Tidak berhasil"** di `progress.md` paling sering dilewat padahal
paling berharga — itu yang mencegah jalan buntu yang sama diulang.

## Kenapa

Tanpa ini, tiap sesi AI baru mulai dari nol dan keputusan yang sudah diambil
hilang. Solusinya bukan memori AI (bisa hilang, tidak terkontrol) — solusinya
berkas di disk yang tetap ada lepas dari model apa yang dipakai.

## Aturan keras: dilarang mengarang kemajuan

Kalau satu sesi tidak menghasilkan keputusan, `decisions.md` **tidak
bertambah**. Memori yang melaporkan kemajuan palsu lebih buruk daripada tidak
ada memori — keputusan berikutnya akan didasarkan pada sesuatu yang tidak
pernah terjadi.

## Cara pakai

- **Awal sesi:** baca keempat berkas, perlakukan sebagai sumber kebenaran,
  ringkas (proyek apa, status, langkah terbaik berikutnya, celah konteks) —
  jangan mulai kerja sebelum dikonfirmasi.
- **Akhir sesi:** perbarui keempatnya sebelum selesai. Urutan penting — baca
  di awal, tulis di akhir. Dibalik, hasilnya kosong.

## Gap yang sudah diperbaiki

Cords `AGENTS.md` merujuk `STANDAR.md` tapi sebelumnya tidak punya
salinannya sendiri di repo (ditemukan 2026-08-16). Sudah disalin dari
`Website/slidee/STANDAR.md` ke `Cords/STANDAR.md` pada tanggal yang sama.
