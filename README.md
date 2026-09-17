# DZS Commission Bot V7.4 — Skin Auto Reset + Clean Logs

Bot Discord commission untuk Railway / Render / Pterodactyl.

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

Setelah customer memilih ukuran dan berhasil membuat order, panel Skin otomatis di-refresh sehingga dropdown kembali ke kondisi siap dipakai untuk order berikutnya.

## Workflow
1. Customer pilih jenis commission.
2. Untuk Skin, customer pilih 64×64 / 128×128 / 256×256 / 512×512.
3. Customer isi detail request.
4. Ticket dibuat otomatis dengan order ID `DZS-0001`, `DZS-0002`, dst.
5. Detail notifikasi pembuatan ticket dicatat rapi di `LOG_CHANNEL_ID`.
6. Worker melakukan Claim.
7. Claim otomatis mengubah status menjadi Progress.
8. Worker dapat mengubah status ke Waiting.
9. Worker/Admin menyelesaikan order.
10. Customer memberikan rating 1–5 dan review.
11. Feedback diposting dengan profil/avatar Worker.
12. Setelah feedback berhasil, ticket dihapus setelah 15 detik.
13. Jika ticket sudah Completed tetapi tidak diberi feedback, cleanup otomatis setelah 24 jam.

## Proteksi
- 1 user = 1 ticket aktif.
- Worker wajib Claim sebelum Completed/Close.
- Ticket yang sudah di-claim tidak dapat diambil Worker lain.
- Feedback hanya dapat diberikan customer pemilik order.
- Feedback ganda untuk order yang sama ditolak.
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
