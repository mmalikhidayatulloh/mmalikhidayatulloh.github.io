---
layout: post
---
![logo freeBSD](/assets/IMG/logo-red.png)

* Do not remove this line (it will not be displayed)
{:toc}

Dunia Operating System cukup luas, meskipun sehari-hari kita cuma melihat windows saja, padahal masih banyak OS selain windows seperti OSX atau MacOS, GNU/Linux, Unix, dan masih banyak lagi. Semua itu diawali oleh Unix, baru kemudian muncul berbagai macam OS.

Salah satunya OS freeBSD, berdasarkan penjelasan dari website resmi freeBSD
>FreeBSD is an operating system used to power modern servers, desktops, and embedded platforms. A large community has continually developed it for more than thirty years. Its advanced networking, security, and storage features have made FreeBSD the platform of choice for many of the busiest web sites and most pervasive embedded networking and storage devices.

freeBSD bukan linux dan bukan unix tapi freeBSD termasuk UNIX-LIKE. Artinya mirip Unix, Linux juga termasuk UNIX-LIKE tetapi Linux dan freeBSD tidaklah sama. Untuk mengetahui perbedaan freeBSD dengan OS lain silahkan baca di catatan saya tentang [Perbedaan freeBSD dengan OS lain]().

Langkah-langkah untuk menginstall freeBSD di virtual box sangatlah mudah dan bisa di tonton di video saya [Cara Install freeBSD](https://youtu.be/9K7aISP_oNc)

## Unduh file .iso di official website freeBSD

Buka <https://freebsd.org> Klik `Download FreeBSD`
![freeBSD](/assets/IMG/Screenshot_2021-05-31_15-30-36.png)

Scroll ke bawah dan tentukan versi freeBSD yang ingin di Install, contohnya `FreeBSD 13.0-RELEASE` Pilih `amd64` di bagian _Installer Images_
![FreeBSD](/assets/IMG/Screenshot_2021-05-31_15-33-36.png)

Pilih `FreeBSD-13.0-RELEASE-amd64-disc1.iso` dan `CHECKSUM.SHA256-FreeBSD-13.0-RELEASE-amd64` Kemudian download seperti biasa
![amd64](/assets/IMG/Screenshot_2021-05-31_15-38-00.png)

Setelah diunduh, konfirmasi download dengan membuka terminal dan masuk ke directory tempat `FreeBSD-13.0-RELEASE-amd64-disc1.iso` dan jalankan perintah berikut

```
sha256sum FreeBSD-13.0-RELEASE-amd64-disc1.iso
```

Hasilnya
![hasil](/assets/IMG/Screenshot_2021-05-31_15-49-01.png)

Pastikan cocok dengan file `SHA256-FreeBSD-13.0-RELEASE-amd64` yang telah diunduh sebelumnya
![cocokan](/assets/IMG/Screenshot_2021-05-31_15-51-22.png)

## Konfigurasi Virtual-box

Buka virtualbox dan Klik `New`
![](/assets/IMG/Screenshot_2021-05-31_16-31-21.png)

Ketikkan namanya `freeBSD` secara otomatis konfigurasinya menyesuaikan, kemudian klik `Next>`
![](/assets/IMG/Screenshot_2021-05-31_16-32-54.png)

Sesuaikan ukuran RAM, karena freeBSD cukup ringan jadi di sini saya hanya mengalokasikan 1 GB = 1024 MB kemudian klik `Next>`
![](/assets/IMG/Screenshot_2021-05-31_16-35-17.png)

Kemudian `Create`
![](/assets/IMG/Screenshot_2021-05-31_16-38-44.png)

Kemudian `Next>`
![](/assets/IMG/Screenshot_2021-05-31_16-39-52.png)

Kemudian `Next>`
![](/assets/IMG/Screenshot_2021-05-31_16-41-15.png)

Sesuaikan penyimpanan yang akan digunakan, di sini saya mengalokasikan 11 GB saja, Kemudian klik `Create`
![](/assets/IMG/Screenshot_2021-05-31_16-42-18.png)

Kemudian Klik `Settings`
![](/assets/IMG/Screenshot_2021-05-31_16-45-28.png)

Kemudian Lakukan seperti berikut ini
![](/assets/VID/simplescreenrecorder-2021-05-31_16.51.15.gif)

Setelah itu klik `Start` dan Jika muncul seperti ini klik `Start` lagi
![](/assets/IMG/Screenshot_2021-05-31_17-00-11.png)

Setelah tampilannya seperti ini tekan `Enter` di keyboard
![](/assets/IMG/Screenshot_2021-05-31_17-06-51.png)

Tekan `Enter` untuk Install
![](/assets/IMG/Screenshot_2021-05-31_17-09-28.png)

Tekan `Enter` untuk Select
![](/assets/IMG/Screenshot_2021-05-31_17-11-29.png)

Ketik `hostname` sesuai keinginan kemudian klik `Enter`
![](/assets/IMG/Screenshot_2021-05-31_17-13-44.png)

Pilih `lib32` (untuk `ports` dan `src` sifatnya opsional), untuk memilih dan tidaknya dengan  cara `menekan spasi pada keyboard` dan `menekan tombol atas bawah pada keyboard` untuk navigasinya. Kemudian tekan `Enter`
![](/assets/IMG/Screenshot_2021-05-31_17-16-13.png)

Pilih `ZFS` atau `UFS` sesuai keinginan, di sini saya memilih `ZFS`. Tekan `Enter` untuk lanjut
![](/assets/IMG/Screenshot_2021-05-31_17-21-02.png)

Tekan `Enter` saja
![](/assets/IMG/Screenshot_2021-05-31_17-23-25.png)

Tekan `Enter` lagi
![](/assets/IMG/Screenshot_2021-05-31_17-24-32.png)

Tekan `Spasi pada keyboad` untuk ceklist kemudian tekan `Enter` untuk lanjut
![](/assets/IMG/Screenshot_2021-05-31_17-25-51.png)

Pilih `YES` (untuk navigasi menggunakan `tombol kanan-kiri-atas-bawah pada keyboard`) kemudian klik `Enter`
![](/assets/IMG/Screenshot_2021-05-31_17-28-59.png)

Tunggu proses installasi
![](/assets/IMG/Screenshot_2021-05-31_17-30-09.png)

Setelah selesai otomatis akan seperti ini, masukkan `kata sandi root` sesuai keinginan. kemudian tekan `Enter`
![](/assets/IMG/Screenshot_2021-05-31_17-31-47.png)

Tekan `Enter` saja
![](/assets/IMG/Screenshot_2021-05-31_17-33-42.png)

Tekan `Enter` untuk `YES`
![](/assets/IMG/Screenshot_2021-05-31_17-34-57.png)

Tekan `Enter`
![](/assets/IMG/Screenshot_2021-05-31_17-35-48.png)

Pilih `No`
![](/assets/IMG/Screenshot_2021-05-31_17-38-31.png)

Tekan `Tab` dan `Enter`
![](/assets/IMG/Screenshot_2021-05-31_20-18-55.png)

Pilih `Asia`
![](/assets/IMG/Screenshot_2021-05-31_17-41-46.png)

Pilih Negara tercinta
![](/assets/IMG/Screenshot_2021-05-31_17-42-40.png)

Sesuaikan dengan zona waktu anda
![](/assets/IMG/Screenshot_2021-05-31_17-43-45.png)

Tekan `Enter`
![](/assets/IMG/Screenshot_2021-05-31_17-44-42.png)

Pilih `Set Date` (Jika tanggal dan waktu tidak sesuai silahkan tekan `tab` untuk mengaturnya)
![](/assets/IMG/Screenshot_2021-05-31_17-45-53.png)

Tekan `Enter`
![](/assets/IMG/Screenshot_2021-05-31_17-49-30.png)

Ceklist `disable sendmail`
![](/assets/IMG/Screenshot_2021-05-31_17-50-13.png)

Tekan `Enter` untuk membuat `user biasa`
![](/assets/IMG/Screenshot_2021-05-31_17-51-54.png)

Lakukan seperti berikut

```
isi username
isi fullname
enter
isi wheel
enter terus sampai enter password baru diisi
enter
ketik yes
ketik no

```

![](/assets/VID/simplescreenrecorder-2021-05-31_17.53.25.gif)

Tekan `Enter`
![](/assets/IMG/Screenshot_2021-05-31_18-02-23.png)

Pilih `No`
![](/assets/IMG/Screenshot_2021-05-31_18-04-17.png)

Pilih `Reboot` dan dengan segera lepas file .iso dari virtualbox
![](/assets/VID/simplescreenrecorder-2021-05-31_18.06.52.gif)

Jika tampilan setelah `Reboot` seperti ini artinya proses installasi berhasil dan tinggal masukkan username dan password
![](/assets/IMG/Screenshot_2021-05-31_18-12-03.png)

# Finish
