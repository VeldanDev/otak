# Jangan memoles sesuatu yang belum pernah dilihat pengguna

**Sumber:** `Website/slidee/docs/memory/` + `Cords/docs/memory/STATUS.md`
("Ini persis pola Slidee" — dikutip persis, disebut dua kali di sumber
Cords).

## Polanya

Slidee dibangun sampai **selesai dan live**, identitas visual final, animasi
halus, SEO terpasang — tapi berhenti **sebelum ada satu pun pengguna
pertama**. Per 2026-08-16, Slidee masih nol pendaftar waitlist. Hambatan
sebenarnya bukan pernah teknis; selalu distribusi.

## Bagaimana Cords sengaja dirancang untuk tidak mengulanginya

- **D-003:** distribusi (`@veldorable`) diputuskan **sebelum** kode ditulis,
  bukan dipikirkan setelah situs jadi.
- Fase prototipe Cords ditutup paksa begitu pertanyaan desain terjawab:
  `STATUS.md` Cords menulis eksplisit "Fase prototipe: SELESAI. Jangan
  diteruskan" — supaya tidak jatuh ke jebakan yang sama (memoles sesuatu yang
  belum dilihat pengguna).
- D-034 (lapisan gerak/animasi Cords) dicatat jujur sebagai **pengecualian**
  yang dikerjakan sebelum ada konten sungguhan, "melawan urutan yang
  disarankan (konten dulu, poles kemudian)" — supaya kalau rilis tertunda,
  sebabnya bisa dilihat, bukan ditebak.

## Cara pakai

Kalau diminta memoles UI/animasi/detail visual pada proyek yang **belum**
punya pengguna nyata: tanya dulu apakah ini menunda langkah menuju pengguna
pertama. Bukan larangan mutlak (Cords tetap mengizinkan pengecualian sadar),
tapi harus jadi keputusan eksplisit yang dicatat di `decisions.md`, bukan
default.

Prinsip yang sama muncul di `STANDAR.md` Bagian 4 (pelajaran Y Combinator):
"rilis sekarang, jangan tunggu sempurna" dan "sepuluh user yang cinta
produknya dulu, baru sistem".
