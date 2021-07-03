---
layout: post
---
* toc
{:toc}

Teknik yang termasuk sangat dasar dalam hal database adalah bagaimana kita membuat database baru. Bisa menggunakan mode CLI yaitu lewat terminal dan yang kedua mengguanakan GUI salah satunya menggunakan phpMyAdmin. Secara kecepatan tentu metode CLI lebih unggul, cukup dengan beberapa baris perintah saja database baru bisa dibuat. Tetapi tentu tidak semua orang suka CLI, beberapa orang sukanya menggunakan GUI agar bisa klik-klik saja biar mousenya tidak nganggur hehe becanda.

Untuk bisa membuat database menggunakan mode GUI tentu kita harus sudah punya dulu softwarenya. Software yang akan saya gunakan pada kesempatan ini adalah `phpMyAdmin`.

# Persyaratan
## 1. Web Server (Apache MariaDB PHP)
## 2. phpMyAdmin
# Cara Kerja
## 1. Buka phpMyAdmin
```
localhost/phpMyAdmin
```
## 2. Login Sebagai super user (root)
## 3. Klik Databases

![masuk ke databases](/assets/IMG/Screenshot_20210704_023629.png)

## 4. Isi nama database baru 

![nama](/assets/IMG/Screenshot_20210704_024329.png)

kemudian klik tombol `Create`

Jika muncul seperti ini silahkan abaikan karena kita akan membuat database kosong, langsung klik menu `home` saja.

![home](/assets/IMG/Screenshot_20210704_024601.png)
## 5. Masuk menu `User accounts`

![user account](/assets/IMG/Screenshot_20210704_024747.png)

Scroll ke bawah dan klik `Add User account`

![adduser](/assets/IMG/Screenshot_20210704_024923.png)

## 6. Isi informasi account
Misalnya di sini saya mengisi
```
usernamenya          -> admin-database
hostnamenya pastikan -> local : localhost
passwordnya terserah
```

![infoaccount](/assets/IMG/Screenshot_20210704_025116.png)

Kemudian scroll ke bawah klik `Go`

![go](/assets/IMG/Screenshot_20210704_025644.png)

## 7. Pilih database

![pilih](/assets/IMG/Screenshot_20210704_025725.png)

Pilih databasenya, misalnya di sini saya memilih `databasebaru` kemudian `Go`

![pilih database](/assets/IMG/Screenshot_20210704_025959.png)

## 8. Cek all
pilih `check all`

![cek all](/assets/IMG/Screenshot_20210704_030143.png)

kemudian klik `Go`

## 9. Selesai
username, database, dan hostname bisa langsung digunakan
