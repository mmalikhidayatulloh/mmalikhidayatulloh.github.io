---
layout: post
---
![anaconda](/assets/IMG/Screenshot_2021-05-29_21-56-18.png)

* Do not remove this line (it will not be displayed) 
{:toc}

Anaconda sering digunakan untuk data science karena di dalamnya tersedia berbagai macam tools untuk keperluan data science seperti jupyter notebook, jupyter-lab, spyder, R, dan lain-lain.

### Kunjungi [website Anaconda](https://anaconda.com)
klik `get started` pilih `Downloads anaconda installer` kemudian scroll ke bawah dan pilih di bagian linux `64-Bit (x86) Installer` dan lakukan download file dengan ekstensi `.sh`
### Install dependensi yang dibutuhkan
silahkan kunjungi [dokumentasi anaconda](https://docs.anaconda.com) klik `Anaconda Individual Editions` kemudian klik `Installations` kemudian scroll sedikit dan klik `Installing on Linux`, sesuaikan dengan distro linux yang digunakan dan install dependensi lewat terminal linux.
### Cek shell yang digunakan oleh terminal
```
$ echo $SHELL
```
biasanya shell yang digunakan adalah `bash` tapi ada juga yang `zsh`
### Installasi
Jika menggunakan jenis shell `bash` maka di depan ada perintah `bash` dan jika `zsh` makan kata `bash` diganti dengan `zsh`
```
$ bash ~/Downloads/Anaconda-version-Linux-x86.sh
```
### Ikuti saja langkah-langkahnya
Defaulnya jika diminta `yes/no` jawab saja dengan `yes`
### Setelah terinstall, tutup terminal dan masuk kembali ke terminal
>Jika sudah ada tulisan `base` artinya anaconda sudah otomatis siap digunakan, tetapi jika tidak ada tulisan `base` di terminal maka anaconda harus di panggil dulu

```
$ conda activate
```
>Dan jika anda ingin agar anaconda atau tulisan `base` tidak otomatis muncul setiap kali anda membuka terminal atau ingin seperti terminal biasa maka jalankan perintah berikut

```
$ conda config --set auto_activate_base false
```
### Jalankan anaconda
Pastikan sudah ada tulisan `base` di terminal
```
$ anaconda-navigator
```
