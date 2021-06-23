---
layout: post
---

* Do not remove this line (it will not be displayed)
{:toc}

## Pendahuluan

Proses itu ada dua macam, ada proses di latar belakang dan proses di depan. Ibaratnya seperti kerja otot, ada yang sadar dan ada yang tidak sadar. Misalnya dalam kehidupan kita, jantung yang berdetak sendiri tanpa kita suruh jantung tetap berdetak, dalam komputer proses seperti itu disebut proses latar belakang atau istilahnya `daemons`, contohnya sshd, huruf `d` ini menunjukkan bahwa ssh termasuk ke dalam proses latar belakang.

Untuk dapat menjalankan proses latar belakang menggunakan `init process` seperti `systemd`, `sysVinit`, `init.d` dan lainnya. Umumnya linux-linux sekarang menggunakan `systemd`. Untuk menggunakan `systemd` menggunakan perintah `systemctl`

## Systemctl

Proses yang akan dijalankan misalnya `ssh`

### Memulai Secara Manual

```
sudo systemctl start sshd
```

### Status

```
sudo systemctl status sshd
```

### Agar Otomatis Berjalan Ketika Komputer di Hidupkan

```
sudo systemctl enable sshd
```

### Cek Layanan yang Berjalan

```
systemctl list-units --type=service
```

### Cek error

```
sudo journalctl
```

### Cek error pada service tertentu

```
sudo journalctl -u sshd.service --no-pager
```

## Proses Latar Belakang

### Menyimpan proses ke latar belakang

misal kita sedang mengetik menggukan `vim` kemudian kita ingin kembali ke terminal tanpa mengakhiri vim. Untuk melakukannya

```
[CTRL] + Z
```

Outputnya

```
[1]  + 13943 suspended  vim
```

### Kembali menjadi latar depan

untuk kembali ke vim

```
fg
```

### Melihat proses yang disimpan ke latar belakang

```
jobs
```

### Menjalankan proses ke latar depan dari banyak proses latar belakang

Misalnya ada 5 proses yang disimpan di latar belakang dan kita ingin membuka proses 2 ke latar depan

```
fg 2
```

### Menjalankan banyak proses secara berurutan

#### Menggunkan semicolon (;)

```
sudo zypper ref ; sudo zypper up
```

#### Menggunakan (&&)

```
sudo zypper ref && sudo zypper up && sudo zypper dup
```
