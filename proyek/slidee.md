# Slidee

Sumber: `Website/slidee/docs/memory/{README,STATUS,progress,decisions}.md`,
`Website/slidee/AGENTS.md`. Update terakhir sumber: 2026-08-16.

## Apa

Landing page pra-rilis (dengan waitlist) untuk **Slidee**, alat penjadwalan
konten untuk kreator solo: satu konten masuk, dipecah jadi empat format sesuai
platform (TikTok, YouTube, Instagram, LinkedIn), user meninjau dan menyetujui,
lalu masuk slot jadwal. Aplikasinya sendiri **belum dibangun** — repo ini
cuma situsnya.

Prinsip yang tak boleh dilanggar: *"Slidee menyiapkan, user yang
menerbitkan."* Slidee tidak memposting otomatis ke platform manapun — itu
butuh izin API tiap platform dan sengaja ditaruh di kolom "Belum" pada situs.

Untuk siapa: kreator solo yang memegang semua platform sendiri. Bukan tim,
bukan agensi.

## Stack

Next.js 16.2.12 (App Router) · React 19.2.4 · TypeScript 5 · Tailwind v4 ·
Vercel. Lima dependency runtime: `next`, `react`, `react-dom`,
`framer-motion`, `lenis` (dua terakhir ditambah sengaja untuk sistem gerak,
lihat `decisions.md` 2026-08-16). Tanpa database/Prisma/ORM/auth — waitlist
lewat Formspree.

Repo privat: `github.com/VeldanDev/slidee`. Live di
`slidee-dusky.vercel.app`.

## Status (per 2026-08-16)

Situs selesai secara fungsional: semua section jalan, identitas visual final
(ikon 4a, wordmark 1e opsi B), animasi masuk + smooth scroll (Lenis) +
parallax terbatas terpasang, SEO dasar + Search Console terverifikasi,
security header terpasang, waitlist tersambung Formspree dan teruji di
produksi.

**Belum ada satu pun pendaftar waitlist.** Hambatan sebenarnya bukan
teknis — situsnya sudah selesai — tapi membawa orang ke situs dan
membuktikan ada yang mau daftar. Satu-satunya saluran distribusi:
`@veldorable` (TikTok).

Nama "Slidee" sudah dicek dan dianggap aman dipakai (2026-08-08) — belum ada
produk aktif dengan nama itu, `slidee.id` tersedia, PDKI belum sempat dicek
karena situsnya bermasalah saat itu (risiko dinilai kecil).

## Bug diketahui, belum diperbaiki

`components/waitlist.tsx` — input honeypot `_gotcha` diposisikan
`absolute left-[-9999px]` tanpa leluhur `position: relative`, jadi containing
block-nya jatuh ke dokumen, bukan ke form. Ditemukan, tidak dikerjakan.

## Langkah berikutnya

Sesuai `STATUS.md` per 2026-08-07: **cek ketersediaan nama "Slidee"** di
domain (.com/.id/.app), Google, App Store, dan PDKI
(pdki-indonesia.dgip.go.id) — sebagian sudah dijawab di keputusan 2026-08-08
di atas, tapi cek PDKI tertunda karena situsnya bermasalah saat itu; belum
diketahui apakah sudah dicek ulang sejak itu.

Kalau ada perkembangan setelah 2026-08-16, `docs/memory/STATUS.md` di repo
Slidee sendiri lebih akurat daripada ringkasan ini.
