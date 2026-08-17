# Hero produk scroll-3D — cara bikin murah/gratis

**Sumber:** `D:\Downloads\Tiburon\03-hasil-analisis\analisis-video.md`, entri
video `tutorwebprem.mp4` (screen-record 45 detik, contoh situs demo
**DriveImport**). Pola yang sama juga muncul di
`o4pRAfEgqNUeDoUo3LnpE9IUkGbLesA2rAChAo.mp4` (efek scroll-reveal
**BuildorasHome**) — **dua sumber independen**, jadi polanya cukup mapan,
bukan kebetulan satu kreator.

## Resep (4 langkah)

1. **Foto produk yang bagus** — studio, pencahayaan dramatis/gelap. Ini
   jadi bahan mentah untuk animasi, kualitasnya menentukan hasil akhir.
2. **Google Flow** — masukkan foto produk, hasilkan animasi cinematic 3D
   pendek dengan transisi mulus antar frame (contoh prompt yang kepakai:
   orbit 360°, top-down bird's-eye, exploded-view komponen).
3. **EZGIF** (`ezgif.com`, fitur "to JPG" / Video to JPG converter) — video
   hasil Google Flow dipecah jadi **sequence gambar JPG per-frame**, frame
   rate di-set **30 fps**. Ini kuncinya: hasil akhirnya bukan video yang
   diputar linear, tapi kumpulan frame diskrit yang bisa diindeks satu-satu.
4. **Serahkan ke AI coding agent** — upload JPG sequence + asset + prompt ke
   tool coding AI (mis. UI mirip Cursor/Codex-style agent). Agent men-generate
   kode yang me-render **frame sesuai posisi scroll user** — scroll maju
   nampilin frame N+1, scroll mundur balik ke frame N-1. Efeknya: animasi
   produk terasa "reaktif" terhadap scroll, bukan video autoplay.

## Kenapa dipecah jadi JPG, bukan dipakai sebagai video

Video HTML5 tidak punya cara murah/presisi untuk di-seek per-frame mengikuti
scroll delta kecil tanpa jank. Sequence gambar diskrit jauh lebih gampang
dikontrol: tinggal ganti `src` (atau canvas draw) ke frame index yang dihitung
dari scroll position — pola umum untuk scroll-triggered product reveal.

## Cara pakai

Relevan kalau butuh hero produk yang terasa premium tanpa budget videografer
3D/software 3D modeling — baik untuk produk sendiri maupun brief klien agency
yang minta efek "scroll makin ke bawah, produk muter/ke-explode". Palet
gelap-dramatis (studio hitam, fog tipis, lighting volumetric) dicatat di
sumber sebagai pelengkap kesan premium, bukan bagian teknis dari resepnya —
boleh diganti sesuai brand.
