# Tailwind v4 beda dari v3 — data latih AI sering salah

**Sumber:** `Website/slidee/AGENTS.md` § 3 (identik di `Website/AGENTS.md`,
**dikonfirmasi** berkas lama sebelum rename Shiftware → Slidee — berkas itu
sudah diberi catatan usang 2026-08-16, lihat `proyek/slidee.md`).
Dikonfirmasi berlaku di Slidee (Next.js 16.2.12 +
Tailwind v4). Belum dikonfirmasi apakah Cords juga sudah di Tailwind v4 —
`Cords/AGENTS.md` cuma menulis "Tailwind" tanpa versi.

## Yang berubah dari v3

- **Tidak ada `tailwind.config.ts`** — token didefinisikan di CSS lewat
  `@theme`
- Import jadi satu baris: `@import "tailwindcss";` — bukan tiga baris
  `@tailwind base/components/utilities`
- PostCSS lewat `@tailwindcss/postcss`
- Tidak ada `content: []` — deteksi file otomatis, jadi bug "kelas Tailwind
  dinamis ke-purge" dari config lama tidak terjadi lagi
- Token `@theme` otomatis jadi utility: `--color-tinta` → kelas `bg-tinta`,
  `text-tinta` langsung tersedia

## Cara pakai

Sebelum menulis konfigurasi Tailwind atau CSS di proyek yang sudah
dikonfirmasi pakai Tailwind v4 (Slidee): jangan buat `tailwind.config.ts`,
jangan pakai tiga baris `@tailwind` lama. Kalau ragu proyek lain (termasuk
Cords) sudah v3 atau v4, cek `package.json`-nya dulu — jangan asumsikan dari
berkas ini.
