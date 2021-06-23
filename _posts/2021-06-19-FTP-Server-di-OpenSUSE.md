---
layout: post
---

* Do not remove this line (it will not be displayed)
{:toc}

# Installasi

* Buka `Yast`
* Pilih `Software management`
* Klik `view` pilih `pattern`
* Scroll ke bawah dan centang `File Server`
* Klik Tombol `Accept`

# Konfigurasi

* Buka `yast`
* Pada bagian *Network Services* pilih `FTP Server`
* Jika disuruh install `vsftp` klik `ok`
* Pada bagian `Start-up` abaikan saja
* Pada bagian `General` centang `verbose logging` dan pada bagian `Ftp directory for anonymous user` silahkan boleh diubah-ubah sesuai directory yang akan anda share menggunakan ftp
* Abaikan bagian `performa`
* Pada bagian `Authentication` silahkan atur sesuai kebutuhan, misalnya saya mengizinkan `Anonymous dan Authenticated Users` untuk mengakses ftp saya maka saya centang `both`. Dan jika saya tidak ingin ada yang mengupload ke ftp saya maka saya tidak menyentang `Enable upload`
* Abaikan `Expert Setting`
* Setelah itu `Finish`

# Jalankan FTP Server

```
sudo systemctl start vsftpd
```
