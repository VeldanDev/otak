# Typecheck bersih ≠ build lolos; wrapper CSS bisa memotong background

**Sumber:** `Cords/docs/memory/progress.md` (2026-08-08), `Website/slidee/docs/memory/progress.md` + `STATUS.md` (2026-08-07).

## Next.js App Router: typecheck bukan jaminan `next build` lolos

Di Cords, dua bug lolos typecheck tapi menggagalkan `next build`:

- **Hydration mismatch** — `innerWidth` dipakai saat render di
  `components/Plane.tsx`, padahal nilai itu tidak ada di server. Perbaikan:
  render nilai yang bergantung ukuran layar **setelah** mount, bukan saat
  render pertama.
- **`useSearchParams` tanpa `Suspense`** — lolos typecheck, gagal di
  `next build`. Perbaikan: pecah halaman jadi server + client component,
  bungkus bagian yang pakai `useSearchParams` dengan `Suspense`.

Pelajarannya: aturan Next.js App Router (Suspense boundary, batas
server/client) hanya benar-benar ditegakkan saat `next build`, bukan saat
typecheck. **Jalankan `next build` sebelum melapor selesai**, jangan
berhenti di typecheck bersih.

## Wrapper max-width yang membungkus SEMUA section memotong background

Di Slidee, satu wrapper `mx-auto max-w-[1120px] bg-kertas` di `page.tsx`
membungkus **seluruh** section sekaligus — akibatnya warna latar tiap
section terpotong sebelum tepi layar, bukan membentang penuh selebar layar
seperti yang diinginkan.

Pola yang benar: `bg-*` dipasang di elemen `w-full` **terluar tiap
section**, dan `max-w-[...] mx-auto` hanya untuk membatasi lebar **isi** di
dalamnya. Satu wrapper global untuk semua section adalah bug, bukan
shortcut yang aman.

## Cara pakai

- Proyek Next.js App Router: jangan anggap selesai dari typecheck saja,
  jalankan `npm run build` (atau setara) sebelum klaim beres.
- Kalau background section terlihat terpotong/tidak full-bleed padahal
  class-nya `w-full`, cek dulu apakah ada wrapper `max-w-*` di level lebih
  luar yang membungkus banyak section sekaligus.
