# DZS Commission Bot V7.5 — MULTI-TICKET

Bot Discord commission untuk Railway / Render / Pterodactyl.

## V7.5 — Multi-Ticket
- Customer **boleh membuat beberapa ticket/order aktif sekaligus**.
- Setiap order memiliki channel ticket dan nomor order sendiri: `DZS-0001`, `DZS-0002`, dst.
- Ticket/order lain milik customer tidak ikut tertutup atau terhapus saat satu order selesai.
- Tidak ada lagi pembatasan **1 user = 1 ticket aktif**.

## Setup command
- `/setup-commission skin`
- `/setup-commission render`
- `/setup-commission logo`
- `/setup-commission animasi`
- `/setup-feedback`

## Skin selector
Panel Skin menyediakan pilihan:
- 64×64
- 128×128
- 256×256
- 512×512

Setelah order Skin dibuat, panel tetap aktif dan siap dipakai untuk order berikutnya.

## Workflow
1. Customer pilih jenis commission.
2. Untuk Skin, customer pilih 64×64 / 128×128 / 256×256 / 512×512.
3. Customer isi detail request.
4. Ticket dibuat otomatis dengan order ID unik berurutan.
5. Detail notifikasi pembuatan ticket dicatat rapi di `LOG_CHANNEL_ID`.
6. Customer masih bisa membuat order/ticket lain tanpa menunggu order pertama selesai.
7. Worker melakukan Claim.
8. Claim otomatis mengubah status menjadi Progress.
9. Worker dapat mengubah status ke Waiting.
10. Worker/Admin menyelesaikan order.
11. Customer memberikan rating 1–5 dan review.
12. Feedback diposting dengan profil/avatar Worker.
13. Setelah feedback berhasil, ticket yang bersangkutan dihapus setelah **15 detik**.
14. Jika ticket sudah Completed tetapi tidak diberi feedback, cleanup otomatis setelah 24 jam.

## Proteksi
- **Multi-ticket aktif per customer** didukung.
- Worker wajib Claim sebelum Completed/Close.
- Ticket yang sudah di-claim tidak dapat diambil Worker lain.
- Feedback hanya dapat diberikan customer pemilik order.
- Feedback ganda untuk order yang sama ditolak.
- Setiap ticket diproses berdasarkan `channel_id` dan `order_id` sendiri.
- Ticket bersifat private.
- Tidak menggunakan Privileged Gateway Intents.

## Railway variables
```env
DISCORD_TOKEN=PASTE_BOT_TOKEN_HERE
GUILD_ID=PASTE_SERVER_ID_HERE
TICKET_CATEGORY_ID=PASTE_TICKET_CATEGORY_ID_HERE
FEEDBACK_CHANNEL_ID=PASTE_FEEDBACK_CHANNEL_ID_HERE
LOG_CHANNEL_ID=PASTE_LOG_CHANNEL_ID_HERE
STAFF_ROLE_ID=PASTE_STAFF_ROLE_ID_HERE
```

Bot membutuhkan permission Discord untuk melihat/mengirim pesan, embed, membaca history, mengelola pesan, serta **Manage Channels** untuk membuat dan menghapus ticket.
