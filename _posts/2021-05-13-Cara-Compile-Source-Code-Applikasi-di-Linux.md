---
layout: post
---
![Gambar](https://images.theconversation.com/files/169396/original/file-20170515-7005-1kosyny.jpg?ixlib=rb-1.1.0&rect=0%2C471%2C5000%2C2425&q=45&auto=format&w=1356&h=668&fit=crop)

* Do not remove this line (it will not be displayed) 
{:toc}

_Tutorial ini pernah saya praktikan untuk menginstall pspp_

Karena kita di dunia source code maka Banyak cara untuk menginstall package (kita menyebutnya package bukan aplikasi) yang kita butuhkan. Bisa lewat package manager seperti `apt-get` untuk basis Debian, `pacman` untuk basis Arch, `dnf` untuk basis redHat, `zypper` untuk SUSE, dan beberapa package manager lain. Kadang kala kita membutukan package tertentu tapi ketika menggunakan package manager tidak tersedia karena package manager itu mengambil database utama yang di sediakan masing-masing distro. Ketika hal ini terjadi maka masih banyak cara untuk mendapatkan package yang kita butuhkan seperti:
1. Download langsung dari website resminya (bentukya biasanya dengan format `.deb` , `.rpm`, `.tar.gz`, dll). Kemudian install sendiri dengan `dpkg`, `rpm`, `dnf`, `zypper`, `yast2`, dll.
2. Pasang alamat repository ke `source.list` kemudian install menggunakan package manager
3. Download dari package downloader seperti `synaptic`, `octopi`, `pamac`, `gnome-software`, dll.
4. Download dari snap menggunakan `snapd`, flatpack menggunakan `flatpak`, AUR (Arch User Repository) dengan `yay` atau manual.

Setelah dari semua itu masih belum didapatkan maka kita bisa langsung ambil _source code_ nya terus kita install sendiri ke komputer kita,jangan lupa bahwa kita di dunia _source code_ dimana kita bebas untuk membuka, mengembangkan, membuat ulang _source code_ yang telah ada karena kita di FOSS (Free Open Souce Software) yang artinya _Freedom_ yaitu kebebasan bukan *Tak berpenghasilan*.

Untuk mengcompile sendiri _source code_ kita butuh _source code_ nya, kemudian koneksi internet, kemudian kopi atau teh dan snack atau kuaci, wkwkwk. Karena butuh kesabaran. ok, langsung saja ikuti langkah-langkahnya kemudian beritahu kalo ada apa-apa.
***
### Download source code dari website yang Anda ingin install
Karena banyak source code yang di publikasikan di github, maka kita butuh package `git` untuk mengambil _source code_ nya. Biasanya menggunakan perintah:

    $ git clone https://github.com/blablablabla

Jika menggunakan `git clone` folder langsung siap digunakan (bisa langsung ke langkah 3), tapi jika tidak menggunakan git clone biasanya harus di download dalam bentuk file archive atau file kompresi.


 Format file yang di download bisa bermacam-macam dan biasanya dalam bentuk file kompresi. Misalnya `.tar` `.tar.gz` `.zip` `.rar` dan format file-file kompresi lainnya.
### Ekstrak file yang telah di download
untuk format `.tar` dan `.tar.gz`

`tar -zxfv namafile.tar`    

untuk format `.rar` pastikan sudah terinstall package(aplikasi) `unrar`

`unrar x namafile.rar`

untuk format `.zip`

`unzip namafile.zip`

untuk format file lain bisa dicari sendiri tutorialnya
### Masuk ke foldernya

`cd namafolder/`

### Pastikan package yang dibutuhkan untuk mengcompile sudah terinstall
package utama yang dibutuhkan `gcc`:

>Untuk distro Debian dan turunannya membutuhkan:
build-essential
Untuk distro Arch dan turunannya membutuhkan:
base-devel
Untuk distro redHat dan turunannya sudah tersedia di group "Development tools" silahkan di install groupnya

### Cek apakah sudah siap atau butuh dependensi lain
sebelum mengcompile, beberapa package masih membutuhkan dependensi tertentu, untuk mengeceknya silahkan jalankan perintah berikut:

    ./configure


Tunggu prosesnya

Jika belum siap maka akan muncul perintah untuk menginstall dependensi yang dibutuhakan, silahkan cari dependensi yang dibutuhkan kemudian install dependensinya dan cek lagi dengan perintah `./configure` sampai dinyatakan siap untuk mengcompile. 
### Proses compile
Jalankan perintah:

    $ make


Tunggu prosesnya

Kemudian jadi super-user/user-root/su atau bisa dengan sudo 

    $ sudo make install clean


Tunggu prosesnya
Jika berhasil maka akan ada pemberitahuan bahwa package telah terinstall, bisa langsung di cek di menu aplikasi.

[cara uninstall]()
