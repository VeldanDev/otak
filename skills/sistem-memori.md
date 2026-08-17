# Sistem memori proyek

**Sumber:** `STANDAR.md` Bagian 1. Latar belakang lengkap:
[pelajaran/sistem-memori-proyek.md](../pelajaran/sistem-memori-proyek.md).

## Kapan dipakai

Proyek apa pun yang dikerjakan lintas sesi AI. **Tidak pernah dilewati** —
satu dari empat aturan yang selalu berlaku apa pun yang dibangun.

## Input

- Apakah `docs/memory/` sudah ada di repo ini?
- Kalau belum: nama proyek, untuk siapa, kenapa penting.

## Langkah

1. Kalau `docs/memory/` belum ada, buat empat berkas:
   - `README.md` — apa proyek ini, untuk siapa, di mana dipublikasikan,
     kenapa penting, **apa hambatan sebenarnya** (biasanya bukan yang
     kelihatan dulu)
   - `STATUS.md` — sudah selesai apa, sedang dikerjakan apa, **satu**
     langkah berikutnya, blocker, pertanyaan terbuka
   - `progress.md` — catatan kerja per sesi, terbaru di atas
   - `decisions.md` — satu keputusan per entri: apa, kenapa, apa yang
     ditolak
2. **Awal sesi:** baca keempat berkas, perlakukan sebagai sumber
   kebenaran, ringkas (proyek apa, status, langkah terbaik berikutnya,
   celah konteks) sebelum mulai kerja.
3. **Akhir sesi:** perbarui keempatnya. Urutan penting — baca di awal,
   tulis di akhir. Dibalik, hasilnya kosong.
4. **Aturan keras:** kalau sesi ini tidak menghasilkan keputusan,
   `decisions.md` tidak bertambah. Jangan mengarang kemajuan yang tidak
   terjadi.

## Contoh

Format satu entri `progress.md`:

```
## 2026-08-17
Dikerjakan:
Diubah:
Dicoba:
Tidak berhasil:
Dipelajari:
Berikutnya:
```

Bagian **"Tidak berhasil"** paling sering dilewat padahal paling
berharga — itu yang mencegah jalan buntu yang sama diulang tiga bulan
lagi.

## Format keluaran

- Struktur folder: `docs/memory/{README,STATUS,progress,decisions}.md`
- Ringkasan awal sesi: 4 poin (proyek apa / status / langkah berikutnya /
  celah konteks)
- Update akhir sesi: STATUS.md baru + entri progress.md baru + (kalau
  ada) entri decisions.md baru + (kalau arah berubah) update README.md
