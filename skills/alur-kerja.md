# Alur kerja & filosofi lazy senior dev

**Sumber:** `STANDAR.md` Bagian 3 (§ PRD, § Lazy Senior Dev, § Model mana
untuk apa) dan Bagian 4 (§ Urutan berpikir). Contoh penerapan:
`Website/slidee/AGENTS.md` § 4, § 9, § 11.

## Kapan dipakai

Sebelum menulis kode untuk fitur atau perubahan apa pun. Filosofi lazy
senior dev berlaku selalu — satu dari empat aturan yang tidak pernah
dilewati apa pun yang dibangun.

## Input

- Requirement fungsional & non-fungsional yang sudah jelas vs belum
- Apakah ini proyek baru (butuh PRD) atau perubahan di proyek berjalan

## Langkah

1. **Urutan berpikir sebelum kode:**
   1. Requirement fungsional — sistem ini harus bisa apa?
   2. Requirement non-fungsional — berapa user, seberapa cepat, device
      apa, seberapa sering gagal masih boleh?
   3. Komponen — apa bagiannya, bagaimana mereka bicara?
   4. Titik lambat — di mana antrian menumpuk?
   5. **Baru** tulis kode.

   Kalau langkah 1–4 belum jelas, **tanya dulu**, jangan menebak.
2. **Siklus per perubahan:** PLAN → IMPLEMENT → TEST → REVIEW → SECURITY
   → SUMMARY. Satu langkah per sesi, lalu lapor — diff yang tidak bisa
   di-review manusia itu vibe coding berbaju rapi.
3. **Proyek baru:** PRD dulu, wajib, sebelum kode. Frontend dulu sampai
   puas, baru backend dan integrasi — urutan ini paling sering dilanggar
   dan menulis API untuk layar yang belum tentu jadi.
4. **Filosofi lazy senior dev:**
   - YAGNI — jangan bangun yang belum dibutuhkan
   - Reuse sebelum menulis baru; stdlib/yang sudah terpasang sebelum
     dependency baru
   - Menghapus lebih diutamakan daripada menambah
   - Kode paling sedikit yang menyelesaikan masalah adalah kode yang
     benar
5. **Model mana untuk apa:** model paling kuat untuk kerja desain,
   keputusan arsitektur, copy, debugging buntu. **Sonnet** untuk rename,
   tweak CSS, cari-ganti, implementasi yang sudah jelas. Membuang model
   mahal untuk cari-ganti adalah pemborosan paling sering terjadi.

## Contoh

Slidee: "Kerjakan langkah 1–8 selesai (sejak 2026-08-07)... langkah 9–10
belum" — satu langkah per sesi, dicatat, bukan semua sekaligus dalam
satu diff raksasa.

## Format keluaran

Per perubahan: catatan singkat PLAN (apa yang mau dilakukan dan kenapa)
→ diff IMPLEMENT → hasil TEST → catatan REVIEW → cek SECURITY → SUMMARY
1–2 kalimat.
