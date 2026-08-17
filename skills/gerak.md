# Gerak (animasi & transisi)

**Sumber:** `STANDAR.md` Bagian 2 (§ GSAP vs Framer Motion, § Gerakan).
Contoh spesifikasi lengkap: `Website/slidee/AGENTS.md` § 7 (§ Gerak).

## Kapan dipakai

Menambahkan atau meninjau animasi/transisi di UI apa pun — web, app.

## Lewati kalau

Elemen dekoratif tanpa fungsi, atau sudah ada sistem gerak baku di
proyek ini (ikuti itu, jangan mengarang angka baru).

## Input

- Elemen mana yang akan bergerak, dan **kenapa** (harus ada alasan
  fungsional — kalau tidak bisa dijelaskan, jangan pasang)
- Pustaka yang sudah dipakai proyek (GSAP / Framer Motion / lainnya)

## Langkah

1. Pilih pustaka: **GSAP** kalau butuh timeline rumit atau proyek bukan
   React (gratis penuh, disponsori Webflow — timeline, ScrollTrigger,
   performa). **Framer Motion** kalau sudah di React dan animasinya
   sederhana. Jangan tertukar `framer-motion` (npm) dengan framer.com
   (pembuat situs AI beda produk).
2. Tentukan durasi baku per jenis gerak (lihat tabel contoh) — bukan
   angka sembarang per komponen.
3. Satu kurva easing untuk seluruh situs (baku: `ease-out`
   `cubic-bezier(0, 0, 0.2, 1)`). Jangan pakai `ease-in-out`, `linear`,
   atau kurva custom tanpa alasan tertulis.
4. Stagger: gap makin lebar, bukan rata (mis. dasar ~70–90ms, +10ms tiap
   langkah) — dipakai untuk grup elemen yang muncul bersamaan, bukan
   elemen tunggal.
5. Daftar boleh/tidak boleh bergerak:
   - **Boleh:** elemen masuk pertama kali ke viewport (sekali saja,
     `whileInView` + `viewport={{ once: true }}`), state interaktif
     (hover/active/focus-visible), indikator UI kecil.
   - **Tidak boleh:** dekorasi murni, loop tak berhenti, apa pun yang
     berulang di luar interaksi user, apa pun yang menunda pembacaan
     heading/CTA utama.
6. **Wajib** hormati `prefers-reduced-motion` — CSS lewat override
   global; Framer Motion lewat `useReducedMotion()` dan skip animasi
   total (render polos), karena override CSS tidak menjangkau animasi
   yang tidak lewat properti `transition`/`animation`.
7. Smooth-scroll (Lenis) dan parallax: matikan **total**, bukan
   diringankan, saat `prefers-reduced-motion` aktif atau di perangkat
   `pointer: coarse` — dicek sebelum instance dibuat.

## Contoh

Durasi baku Slidee:

| Jenis gerak | Durasi | Jarak | Easing |
|---|---|---|---|
| Masuk saat scroll — heading | 850ms | y 26px | ease-out |
| Masuk saat scroll — body | 700ms | y 16px | ease-out |
| Hover (kartu naik, tombol redup) | 150ms | — | ease-out |
| Tekan/aktif | 150ms | — | ease-out |
| Transisi UI kecil | 150–200ms | — | ease-out |

Parallax dikunci ke kekuatan 0.05–0.06, hanya di elemen paling penting
per section (bukan tersebar) — "nyaris tak terlihat sebagai parallax".

## Format keluaran

Tabel durasi/jarak/easing per jenis gerak siap tempel ke `AGENTS.md`,
plus konfirmasi `prefers-reduced-motion` sudah ditangani di jalur CSS
maupun JS.
