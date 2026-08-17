# Keamanan

**Sumber:** `STANDAR.md` Bagian 8. Contoh penerapan: `Website/slidee/AGENTS.md`
§ 10.

## Kapan dipakai

Apa pun yang bisa dijangkau dari internet, **sekecil apa pun proyeknya**.
Satu dari empat aturan yang selalu berlaku apa pun yang dibangun.

## Input

- Apakah proyek expose endpoint publik?
- Di mana kredensial disimpan (`.env`, `.mcp.json`, secret manager)?

## Langkah

Non-negotiable:

1. Default bind ke `localhost`. Expose ke publik adalah **keputusan
   sadar**, bukan default.
2. Kalau di-expose: wajib auth + password custom sebelum link dibagikan.
3. API key wajib untuk semua endpoint yang bisa dijangkau dari luar.
4. Kredensial **tidak pernah** masuk chat, repo, commit, atau screenshot.
   Kalau terlanjur → **revoke**, jangan rotate diam-diam.
5. `.env` di `.gitignore`, jangan pernah dilepas. `.mcp.json` hanya
   memuat `${ENV_VAR}`, bukan key mentah.
6. Validasi semua input user, sanitasi output.
7. Security header wajib di setiap situs sebelum publikasi:
   `X-Frame-Options`, `X-Content-Type-Options`, `Referrer-Policy`,
   `Permissions-Policy`, `Strict-Transport-Security`, CSP.
8. CSP: `unsafe-eval` hanya di development, **tidak pernah** di
   produksi.
9. Verifikasi header dengan tool eksternal (mis. vibecodercheck.site)
   sebelum bilang selesai.

Untuk aplikasi hasil vibe coding (bukan proyek pribadi kecil), pakai
tool tambahan sesuai kebutuhan: Claude Security (review PR), Strix
(pentest ofensif AI agent), HackAgent (red-team khusus AI
agent — deteksi prompt injection/jailbreak, paling relevan untuk produk
berbasis AI agent).

## Contoh

`next.config.ts` set header, lalu verifikasi lewat scanner eksternal —
begini alurnya di Slidee sebelum deploy, bukan menebak header apa yang
"cukup".

## Format keluaran

Checklist pre-launch:
- [ ] Security header terpasang & terverifikasi
- [ ] Tidak ada kredensial ter-commit
- [ ] CSP tanpa `unsafe-eval` di produksi
- [ ] Endpoint publik punya auth/API key
