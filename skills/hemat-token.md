# Hemat token

**Sumber:** `STANDAR.md` Bagian 3 (§ Hemat token).

## Kapan dipakai

Produk berbasis LLM (bukan situs statis) — terutama yang jalan lama atau
volume request tinggi. Untuk situs statis, lewati.

## Input

- Volume request/hari yang diperkirakan
- Provider LLM yang dipakai saat ini

## Langkah

1. Empat lapis hemat token: kompres output tool → kompres konteks →
   kompres output LLM → bias "lazy senior dev" (jawaban singkat, bukan
   menjelaskan yang sudah jelas dari kode).
2. Ukur token dari hari pertama: input, cached, output, biaya per
   request — jangan tunda sampai biaya sudah membengkak.
3. **Cached token adalah metrik utama**, bukan afterthought — desain
   prompt supaya bagian statis (system prompt, instruksi) di-cache,
   bagian dinamis di akhir.
4. Selalu ada routing layer antara aplikasi dan provider LLM — jangan
   hardcode ke satu vendor, supaya bisa pindah model/harga tanpa rombak
   kode.

## Contoh

Teknik "caveman" — jawaban singkat, hemat token: *"Why use many token
when few token do trick."* Klaim potong ~65% token pada kasus nyata.

## Format keluaran

Dashboard/log token minimal: input, cached, output, biaya per request —
dipantau sejak hari pertama, bukan ditambahkan belakangan.
