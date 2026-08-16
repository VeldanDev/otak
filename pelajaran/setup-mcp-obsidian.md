# Setup MCP Obsidian — cara yang barusan berhasil

**Sumber:** dikonfirmasi jalan di sesi 2026-08-16, dites lewat pembacaan
`INDEKS.md` dan tulisan berkas ini sendiri.

## Ringkasan

MCP server yang dipakai: **`obsidian-mcp-server`** (paket npm), bicara ke
plugin **Local REST API** (Adam Coddington) yang jalan di dalam Obsidian.

## Prasyarat

- Plugin community **Local REST API** (Adam Coddington) terpasang dan aktif
  di vault.
- **Obsidian harus terbuka** saat MCP server dipakai — kalau aplikasinya
  tertutup, request ke REST API gagal dengan `CONNECT_TIMEOUT` (server REST
  API-nya cuma jalan selama Obsidian jalan, bukan proses berdiri sendiri).
- Ambil API key dari pengaturan plugin Local REST API di Obsidian (Settings →
  Local REST API → API Key).

## Jebakan yang ditemukan

- **Alamat yang benar: `https://127.0.0.1:27124`** (HTTPS, port 27124) —
  **bukan** `http://127.0.0.1:27123` (HTTP, port 27123). Port 27123 HTTP itu
  ada tapi bukan yang dipakai konfigurasi ini.
- Plugin Local REST API pakai **sertifikat self-signed**, jadi Node menolak
  koneksi TLS secara default. Perlu `NODE_TLS_REJECT_UNAUTHORIZED=0` di env
  proses MCP server. (Ini melemahkan verifikasi TLS secara umum — cukup
  aman di sini karena tujuannya cuma `127.0.0.1`, jangan dipakai pola yang
  sama untuk koneksi ke host eksternal.)
- Paket **`sams-mcp`** yang disebut di carousel/promosi SAMS **tidak ada di
  npm** — jangan coba pasang itu. Paket yang benar dan tersedia di npm
  adalah **`obsidian-mcp-server`**.

## Konfigurasi yang jalan

Bentuknya (di `mcpServers` config, mis. `.claude.json`):

```json
{
  "obsidian": {
    "type": "stdio",
    "command": "npx",
    "args": ["-y", "obsidian-mcp-server"],
    "env": {
      "OBSIDIAN_API_KEY": "<API key dari Settings > Local REST API di Obsidian>",
      "OBSIDIAN_BASE_URL": "https://127.0.0.1:27124",
      "NODE_TLS_REJECT_UNAUTHORIZED": "0"
    }
  }
}
```

Kalau lewat CLI `claude mcp add`, env yang sama berlaku — intinya tiga
variabel di atas (`OBSIDIAN_API_KEY`, `OBSIDIAN_BASE_URL`,
`NODE_TLS_REJECT_UNAUTHORIZED`) harus diset semua, dan `OBSIDIAN_BASE_URL`
harus persis `https://127.0.0.1:27124`.

**Jangan pernah tulis API key sungguhan ke berkas yang masuk git atau ke
vault** — key di atas sengaja diganti placeholder.

## Cara pakai

Sebelum memasang ulang atau debug MCP Obsidian di mesin lain: cek dulu
Obsidian sedang terbuka, plugin Local REST API aktif, dan tiga env var di
atas benar — terutama alamat `27124` (bukan `27123`) dan paketnya
`obsidian-mcp-server` (bukan `sams-mcp`). Kalau hasilnya `CONNECT_TIMEOUT`,
penyebab paling umum adalah Obsidian tertutup.
