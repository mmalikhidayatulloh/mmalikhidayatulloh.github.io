---
layout: post
---

* Do not remove this line (it will not be displayed) 
{:toc}

Setiap distro linux memiliki package manager masing-masing untuk keperluan memajemen package-package dalam distro tersebut. Beberapa package manager yang pernah saya coba sejauh ini seperti `apt-get` di debian, `pacman` di Arch, `dnf` di redhat, dan `zypper` di openSUSE. Pada dasarnya semua package manager memiliki perintah yang sama, cuma beda dikit-dikit. Pada kesempatan ini saya akan menjelaskan cara menggunakan package manager `zypper` secara sederhana dan yang biasa saya gunakan sehari-hari di openSUSE.

# Refresh Repository
```
sudo zypper ref
```
# List Repository
```
sudo zypper lr
```
# Menambah Repository
```
sudo zypper ar urlRepository namaRepository
```
# Menghapus Repository
```
sudo zypper rr namaRepository
```
# List package yang bisa di upgrade ke versi terbaru
```
sudo zypper lu
```
# Upgrade package ke versi terbaru
```
sudo zypper up
```
# Upgrade distro ke versi terbaru
```
sudo zypper dup
```
# Install Package
```
sudo zypper in namaPackage
```
# Uninstall Package
```
sudo zypper rm namaPackage
```
# Uninstall Package beserta dependensinya
```
sudo zypper rm -u namaPackage
```