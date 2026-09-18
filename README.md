# DZS Commission Bot V5.1 — Ticket & Feedback FIXED

Versi perbaikan dari bot yang dikirim user.

## Perbaikan utama
- Multi-ticket: satu customer dapat membuat banyak order aktif.
- Tombol ticket sekarang membawa `Order ID` sendiri (`DZS-xxxx`) sehingga Claim/Progress/Waiting/Completed/Close tidak tertukar antar ticket.
- Handler juga memverifikasi bahwa Order ID memang milik channel ticket yang sedang dibuka.
- Rating dan modal feedback diverifikasi terhadap order + channel saat ini.
- `TICKET_CATEGORY_ID` di-fetch dari Discord jika belum ada di cache dan harus menunjuk ke Category Channel.
- Feedback menghapus ticket 15 detik setelah feedback berhasil.
- Cleanup ticket completed tanpa feedback tetap berjalan setelah 24 jam.
- Tidak menggunakan privileged gateway intents.

## Railway Variables
```env
DISCORD_TOKEN=...
GUILD_ID=...
TICKET_CATEGORY_ID=ID_CATEGORY_SHOPS
FEEDBACK_CHANNEL_ID=...
LOG_CHANNEL_ID=...
STAFF_ROLE_ID=...
```
`TICKET_CATEGORY_ID` harus ID **kategori** (misalnya kategori `SHOPS`), bukan ID channel `ticket-order-*` atau `ticket-dzs-*`.

## Deploy
Node 20+ dan `npm start`.
Untuk SQLite, gunakan Railway Volume pada `/app/data` agar data order tidak hilang ketika container dibuat ulang.
