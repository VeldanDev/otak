# Membangun produk sendiri (startup)

**Sumber:** `STANDAR.md` Bagian 4.

## Kapan dipakai

Membangun produk sendiri (Slidee, startup AI) — bukan proyek klien
(klien sudah punya bisnis berjalan, lewati bagian YC).

## Input

- Tahap produk (belum launch / sudah ada user / mulai lambat)

## Langkah

1. Tiga pelajaran Y Combinator:
   - **Rilis sekarang**, jangan tunggu sempurna — satu-satunya cara tahu
     masalah user itu nyata atau asumsi. Syarat: harus punya minimal
     satu hal yang benar-benar berguna.
   - **Kerjakan hal yang tidak bisa di-scale** dulu (analogi Airbnb:
     founder memotret listing sendiri satu per satu) — jangan bangun
     otomatisasi sebelum punya sepuluh user yang cinta produknya.
   - **Founder membunuh dirinya sendiri, bukan kompetitor** — hanya dua
     kegiatan penting di early stage: menulis kode dan ngobrol dengan
     user. Konferensi/networking terasa produktif, padahal nol.
2. Checklist scaling — tanya berurutan tiap kali ada yang lambat:
   lambat untuk satu request (performance) → lambat karena banyak
   request (scalability) → ada request berulang/identik (caching) →
   cache hit rendah (bukan caching, cari sebab lain) → job independen
   (parallelization) → job berat memblokir yang lain (message queue).
3. Stack tidak sepenting mengirimkan produk — WhatsApp 900 juta user
   dengan 50 engineer, Uber pindah Python→Go untuk dispatch, semua
   raksasa mulai kecil.

## Contoh

Checklist scaling dipakai sebagai flowchart diagnosis, bukan daftar
solusi yang dipasang sekaligus di awal — pasang caching/queue/parallel
hanya kalau gejalanya memang cocok dengan urutan di atas.

## Format keluaran

Diagnosis satu baris per masalah lambat: gejala → kategori (performance/
scalability/caching/parallelization/queue) → tindakan.
