---
layout: post
---

* Do not remove this line (it will not be displayed)
{:toc}

Salah satu ciri khas dari OS unix-like adalah bisa menginstall aplikasi/package hanya menggunakan terminal, kita menyebutnya package manager. Package manager bisa menginstall, menghapus, dan  mengupdate package dari suatu OS. Package manager ini setiap OS berbeda-beda misalnya pada opensuse menggunakan `zypper`, debian mengguanan `apt`, fedora, redhat, centos menggunakan `dnf`, arch menggunakan `pacman`, di freeBSD menggunaan `pkg`. dan masih banyak package manager lain. Dengan Package manager, ketika kita menginstall package maka seluruh library dan dependensinya sudah otomatis terinstall, Package manager mengambil official repository suatu OS, nah inilah keterbatasan dari package manager. Ketika suatu package tidak ada di official repository maka user perlu cara lain untuk menginstall package yang diinginkan. Dalam freeBSD kebutuhan tersebut sudah disediakan menggunakan `port`, prinsipnya seperti mengcompile source code, tapi port di freeBSD sudah diinstallkan dependensi-dependensinya dan user dapat memilih sesuka hati apa saja yang akan di compile. Berbeda dengan compile linux, ketika di linux `./configure` muncul error karena ada dependensi yang belum diinstall oleh user sebelum user melakukan compile. Kemudian perbedaan lain adalah ketika menggunakan `package` manager maka yang diinstallkan adalah versi tersimple dari suatu package sementara ketika menggunakan `port` maka package sudah versi kompleksnya. kemudian jika menggunakan package manager membutuhkan waktu yang singkat, maka menggunakan port cukup lama untuk menginstall (karena sudah kompleks).

# Package Manager
## Mencari package
```
pkg seacrh namapackage
```
## Update package
```
pkg update
```
## Upgrade package
```
pkg upgrade
```
## Info package tertentu
```
pkg info namapackage
```
## Info package terinstall
```
pkg info
```
## Daftar package utama yang terinstall
```
pkg prime-origins
```
## Install package
```
pkg install namapackage
```
## Remove package
```
pkg remove namapackage
```
## Remove otomasi package yang tidak terpakai
```
pkg autoremove
```
## Bersihkan package versi lama
```
pkg clean
```
# Port
## Install Ports
```
portsnap fetch
```
```
portsnap extract
```
## Update Ports
```
portsnap fetch update
```
## Mencari package yang akan diinstall
misalnya ingin mencari apache
```
whereis apache
```
## Menginstall package
misalnya ingin menginstall apache
```
cd /usr/port/www/apache2.4
```
```
make install clean
```
Jika diminta sesuatu klik saja `enter` sampai package berhasil diinstall
## Uninstall package
masuk ke directory portnya, kemudian
```
make deinstall
```
## Upgrade ports
### Menggunakan pkg
```
pkg version -l "<"
```
### Menggunakan portmaster
```
cd /usr/ports/ports-mgmt/portmaster
```
```
make install clean
```
Setelah terinstall
```
portmaster -a
```
### Menggunakan portupgrade
```
cd /usr/ports/ports-mgmt/portupgrade
```
```
make install clean
```
Setelah terinstall
```
portupgrade -ai
```
# Sumber

[https://docs.freebsd.org/en/books/handbook/ports/](https://docs.freebsd.org/en/books/handbook/ports/)