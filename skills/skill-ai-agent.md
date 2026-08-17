# Skill AI 2026 & aturan membangun AI agent

**Sumber:** `STANDAR.md` Bagian 7.

## Kapan dipakai

Produk berbasis LLM (startup AI) dan perencanaan belajar. Untuk situs
statis, ambil bagian AEO saja (lihat [seo-aeo.md](seo-aeo.md)).

## Input

- Apakah produk melibatkan AI agent yang menjawab dari data (bukan
  cuma chat generik)

## Langkah

1. Tujuh area yang disebut paling menentukan 2026: Context Engineering
   (merancang seluruh konteks — data apa masuk, urutan, **apa yang
   dibuang**, bukan cuma prompt bagus), AI Agents (mengerjakan sampai
   selesai, bukan cuma jawab), Multimodal AI, MCP (standar koneksi AI↔
   tool, sudah jadi standar de facto), RAG (wajib kalau akurasi tidak
   bisa ditawar), AEO, Automation (ROI tercepat, tanpa coding).
2. **Aturan keras membangun AI agent** (paling sering dilanggar):
   - Agent **tidak boleh** menjawab dari ingatan/prompt — ditanya stok,
     wajib cek data; ditanya harga, wajib ambil dari daftar harga.
   - **Jangan** tumpuk semua aturan jadi satu prompt panjang — makin
     panjang, makin bingung agennya. Pakai alur bercabang dengan langkah
     pengambilan data eksplisit.
   - **Selalu** sediakan jalan eskalasi ke manusia — bukan tanda gagal,
     itu yang membuat sistem bisa dipercaya.
   - Orkestrasi multi-agent kalau satu agent tidak cukup.

## Contoh

Agent ditanya "berapa stok barang X" harus memanggil tool/database, bukan
menjawab dari konteks percakapan atau menebak dari pola umum.

## Format keluaran

Untuk tiap kemampuan agent: pertanyaan yang bisa ditanyakan user → tool/
data source yang wajib dipanggil → kondisi eskalasi ke manusia.
