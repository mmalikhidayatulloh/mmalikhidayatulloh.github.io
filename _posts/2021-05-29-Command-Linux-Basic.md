---
layout: post
---
* Do not remove this line (it will not be displayed) 
{:toc}

Karena linux termasuk dalam unix-like, dan unix itu banyak menggunakan `CLI` atau Command Line Interface maksudnya bahwa perintah-perintah yang ingin dijalankan oleh pengguna kepada perangkat komputernya dengan cara mengetikkan kata-kata pada terminal. Awalnya begitu, tapi semakin ke sini user tinggal klik-klik tombol saja, dan metode untuk menjalankan perintah dengan cuma melakukakan klik, drag, pada tombol-tombol yang tersedia menggunakan pointer disebut Graphical User Interface atau biasa disebut `GUI`. 

Meskipun zaman ini sudah sangat-sangat mudah dengan hadirnya `GUI` tapi linux tetap menyediakan `CLI` dengan terminal, ya karena lebih ringan dan lebih profesional. Tetapi saya tidak mengatakan `CLI` lebih baik daripada `GUI` maupun sebaliknya, kareana mereka saling melengkapi satu-sama lain.

Nah tujuan dari tulisan ini yaitu menjelaskan bagaimana cara menggunakan `CLI`, terutaman perintah-perintah apa saja yang digunakan. Kemudian yang perlu diperhatikan adalah perintah-perintah ini hanya bisa digunakan di OS unix-like seperti linux, keluarga BSD, Android juga bisa dikit-dikit menggunakan applikasi `termux` ya karena Android menggunakan kernel Linux, MacOS juga bisa karena di Mac kan ada terminal. Yang tidak bisa itu di `command prompt` atau `CMD` pada perangkat windows.

# Shortcut Terminal

| Shortcut | Fungsi |
| :----- | :------ |
| Ctrl + L | Hapus layar |
| Ctrl + C | Membatalkan perintah yang dijalankan |
| Ctrl + U | Menghapus karakter yang telah diketik di kiri kursor |
| Ctrl + K | Menghapus karakter yang telah diketik di kanan kursor |
| Ctrl + D | Menutup shell |
| Shift + Page Up | Scroll ke atas |
| Shift + Page Down | Scroll ke bawah |
| Tombol Navigasi ke atas dan bawah | Melihat history perintah |

### Untu mengecek jenis `shell` yang digunakan oleh terminal Anda:
```
echo $SHELL
```
### Untuk mengecek `shell` apa saja yang terinstall di teminal Anda:
```
cat /etc/shells
```
### Melihat tanggal hari ini:
```
date
```
### Melihat kalender
```
cal
```
### Melihat kalender pada bulan dan waktu tertentu
```
cal feb 1998
```
### Mengetahui posisi Anda saat ini di dalam terminal
```
pwd
```
### Membuat direktori
```
mkdir namadirectory
```
### Masuk ke directory
```
cd directorytujuan
```
### Melihat isi directory
```
ls
```
### Melihat file tersembunyi pada suatu directory
```
ls -a
```
### Melihat isi directory beserta hak ases file, waktu pembuatan file, pemilik file, grup yang bisa mengakses, ukuran file.
```
ls -l
```
### Menghapus file
```
rm Namafile
```
### Menghapus directory _kosong_
```
rmdir directoryKosong
```
### Menghapus directory yang _tidak kosong_
```
rm -rf directorytidakkosong
```
### Masuk ke directory di atas directory sekarang
```
cd ..
```
### Memindahakan directory
```
mv /directoryyangingindipindah /directorytujuan
```
### Rename file atau directory
```
mv oldname newname
```
### copy file atau directory
```
cp /directoryyangakandicopy /Directorytujuan
```
### Membuat file kosong
```
touch namafile.formatfile
```
### Mengecek pengimpanan internal
```
df -h
```
### Mengecek memory(RAM)
```
free
```
### Menjadi SuperUser(Root)
```
su
```
### Ganti password `su`
```
sudo passwd root
```
### Cek versi OS Anda
```
uname -a
```
### Cek versi distro yang Anda gunakan
```
lsb_release -a
```
### Jika Anda belum tahu tentang command linux yang lain silahkan baca manual page
```
man commandyangingindipelajari
```
misalnya ingin tahu tentang `sudo`
```
man sudo
```
