---
layout: post
---
![zoom](/assets/IMG/ZoomLogo.png)

* Do not remove this line (it will not be displayed) 
{:toc}

Zoom is the leader in modern enterprise video communications, with an easy, reliable cloud platform for video and audio conferencing, chat, and webinars.

Ada banyak cara untuk menginstall zoom di linux. Perlu diketahui bahwa zoom tidak tersedia di repository utama artinya tidak bisa hanya mengandalkan package manager murni. Masing-masing distro linux juga berbeda-beda cara. Sebenarnya memang bisa lewat pihak ketiga seperti snap dan flatpak, tapi saya akan menjelaskan cara yang menurut saya yang terbaik

## Install Zoom di Arch based distributions

Cara install zoom di distro turunan Arch linux bisa lewat AUR. Tapi menurut saya yang terbaik adalah download dari website resmi, dan install menggunakan package manager.

1. Downloads dari [website resmi zoom](https://zoom.us/download).
2. Untuk jenis linuxnya pilih Arch, kemudian klik downloads.
3. Format file yang di downloads adalah `.pkg.tar.xz`
4. Setelah di download, buka terminal kemudian masuk ke directory Downloads dan jalankan perintah

       sudo pacman -U zoom_x86_64.pkg.tar.xz


5. Selesai
6. Untuk Uninstall

       sudo pacman -Rs zoom

## Install Zoom dengan format `.rpm`

Beberapa distro `turunan RHEL` seperti `centos`, `fedora`, dan lain-lain, serta `openSUSE` menggunakan format aplikasi `.rpm`. Untuk menginstallnya:

1. Downloads dari [website resmi zoom](https://zoom.us/download).

2. Untuk jenis linuxnya menyesuaikan (centos, openSUSE, fedora, redHat), kemudian klik downloads.

3. Format file yang di downloads adalah `.rpm`

4. Kemudian juga klik Download Public Key, dan unduh filenya dengan format `.pub`

5. Setelah di download, buka terminal kemudian masuk ke directory Downloads dan jalankan perintah

       sudo rpm --import package-signing-key.pub

    Setelah itu install seperti biasa sesuai package manager masing-masing distro.
    Misalnya pada openSUSE
    ```
    sudo zypper in zoom_openSUSE_x86_64.rpm
    ```


5. Selesai
6. Untuk Uninstall

       sudo zypper rm zoom

## Install Zoom di Debian based distributions

1. Downloads dari [website resmi zoom](https://zoom.us/download).
3. Format file yang di downloads adalah `.deb`
4. Setelah di download, buka terminal kemudian masuk ke directory Downloads dan jalankan perintah

       sudo dpkg -i zoom_amd64.deb


5. Selesai
6. Untuk Uninstall

       sudo dpkg --uninstall zoom
