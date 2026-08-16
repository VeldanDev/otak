# Janji privasi harus ditegakkan di server, bukan cuma UI

**Sumber:** `Cords/docs/memory/decisions.md` D-017, D-023, D-026.

## Keputusan aslinya

D-017: skor minat pengguna tidak pernah diperlihatkan — hanya daftar nama
topik tanpa angka, dengan tombol hapus per topik.

## Kenapa ini butuh entri terpisah (D-023)

Keputusan "tidak diperlihatkan" pada awalnya hanya diterapkan di UI. Itu
tidak cukup: kalau endpoint API tetap mengirim skornya ke klien, siapa pun
yang membuka network tab browser bisa melihatnya — janji privasinya jadi
bohong meskipun UI-nya sendiri tidak menampilkan angka.

Perbaikannya: tabel `affinities` tetap menyimpan skor (dibutuhkan untuk
mengurutkan For Your Coordinates di server), tapi **endpoint hanya
mengembalikan nama topik dan urutannya** — angkanya tidak pernah keluar dari
server.

D-026 mengulang pola yang sama di lapisan lain: `lib/store.tsx` (localStorage
sementara sebelum Supabase siap) sengaja membuat `interests` hanya
mengembalikan nama topik terurut, bukan skornya — supaya aturan yang sama
ditegakkan bahkan sebelum backend sungguhan ada.

## Cara pakai

Kalau sebuah keputusan produk adalah "user tidak boleh melihat X" (skor,
data sensitif, status internal), verifikasi bahwa X memang tidak pernah
dikirim ke klien sama sekali — bukan cuma disembunyikan dari tampilan.
Periksa response API/query, bukan cuma komponen UI yang merendernya.
