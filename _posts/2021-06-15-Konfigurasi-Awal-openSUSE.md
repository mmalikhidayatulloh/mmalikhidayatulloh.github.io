---
layout: post
---
![opensuse wallpaper](/assets/IMG/screenshot.jpg)

* Do not remove this line (it will not be displayed) 
{:toc}

Setelah openSUSE terinstall pada perangkat Anda,maka langkah selanjutnya adalah mengkonfigurasi opensuse agar siap untuk digunakan.

Beberapa hal yang perlu dilakukan sesuai pengalaman saya selama menggunakan openSUSE:

## Refresh repository dan update software

Hal ini penting untuk dilakukan agar package-package yang ada di perangkat yang kita gunakan selalu terbaru agar stabil, keamanan terjamin, serta bug yang sudah di fix sehingga nyaman untuk digunakan (di linux untuk menyebut aplikasi istilahnya package). Pastikan perangkat kita terhubung ke internet agar bisa mengupdate package.

Untuk refresh repositoy kalo di debian `sudo apt-get update` sedangkan di openSUSE

```
sudo zypper ref
```

Setelah repository terupdate baru bisa update package, di debian `sudo apt-get upgrade` sedangkan di openSUSE

```
sudo zypper up
```

## Install codecs

Codecs digunakan agar format-format multimedia seperti `MP3, DVD, DivX, MP4, x265, x264, WMV, WMA, MOV` bisa diputar di media player. Ketika codecs tidak diinstall maka video-video yang anda miliki tidak bisa diputar di media player.

Untuk menginstall codecs:

* Buka `yast`
* Pilih `Software Management`
* Pilih `Configuration`
* Pilih `Repositories`
* Pilih `Add`
* Pilih `Community repositories`
* Pilih `Packman repositories`
* Kemudian `Ok`
* Kemudian di `Software Management` pilih `View`
* Pilih `Repositories`
* Pilih `Packman Repository`
* Pilih tulisan biru `Switch system package`
* Klik tombol `Accept`
* Kemudian `OK`

Untuk KDE dan GNOME bisa dengan sekali klik, caranya:

* Buka [link berikut](https://opensuse-community.org/)
* Pilih `1 clikc install` sesuai jenis desktop environtmen
* Download filenya
* Klik file yang sudah di download maka otomatis akan menuju installer
* Kemudian ikuti langkah-langkahnya

## Install Microsoft Font

Hal yang sangat penting bagi saya adalah font `Times New Roman` hehe. Karena secara default font ini tidak terinstall maka harus diinstall manual dengan cara:

```
sudo zypper in msttcore-fonts
```

## Install package sesuai kebutuhan

Untuk menginstall package di debian dengan cara `sudo apt-get install namapackage` sedangkan di openSUSE bisa dengan 2 cara:

* Cara Pertama: Menggunakan package manager `zypper`

    Install package lewat terminal tentu tidak asing bagi pengguna linux, karena setiap linux dilengkapi package manager. Di debian menggunakan `apt` sedangkan di openSUSE menggunakan `zypper`

    Misalnya install `vlc` (video player favorit saya)

    ```
    sudo zypper in vlc
    ```

    Untuk uninstall package
    * Uninstall biasa
    
    ```
    sudo zypper rm vlc
    ```
    * Uninstall beserta dependensinya

    ```
    sudo zypper rm -u vlc
    ```

* Cara Kedua: Menggunakan `Yast`

    Menurut saya ini cara terbodoh, hehe becanda. Install package tinggal klik

    * Buka `Yast`
    * Ketik package yang ingin diinstall
    * Centang package yang ingin diinstall
    * Klik tombol `Accept`

    Uninstall lewat `yast` juga mudah, tinggal ganti `centang hijau` menjadi `centang merah` kemudian klik tombol `Accept`

## Kustomisasi

Langkah ini terserah hehe. Namanya juga customisasi ya terserah masing-masing ya. Baik itu customisasi tampilan, panel, wallpaper, tema, dan pengaturan-pengaturan lain.
