---
layout: post
---
![openssh](/assets/IMG/openssh.jpeg)

* Do not remove this line (it will not be displayed) 
{:toc}

SSH biasanya digunakan untuk me*remote* komputer ke komputer lain, maksudnya meremote di sini yaitu kita bisa menggunakan/mengakses komputer lain lewat command line. Umumnya dilakukan pada komputer-komputer `unix-like` seperti linux, keluarga BSD (freeBSD, openBSD, nomadBSD, dragonflyBSD) Karena operating sistem jenis ini biasa digunakan sebagai server dan server nggak terlalu peduli dengan `GUI`, semuanya dilakukan dengan `CLI` dan ssh meremotenya juga dengan `CLI` jadi jika anda bergelut di sever maka biasakan dengan `CLI`. openSSH diciptakan oleh orang-orang yang membuat openBSD.

Dewasa ini SSH sangat sering digunakan, misalnya ketika kita membeli VPS maka kita akan mendapat alamat ip dari provider. Sederhananya ketika membeli VPS itu seperti menyewa komputer tapi komputernya virtual (aneh kan) bukan komputer visik, tapi meskipun komputernya tidak bisa kita pegang tetapi komputer itu ada dan bisa digunakan. Nah untuk mengakses komputer virtual tersebut menggunakan SSH.

Untuk menjadi SSH server di linux apapun caranya sama. Normalnya sudah terinstall secara otomatis ketika menginstall linux

## Install openssh
Package `openssh` dapat diinstall menggunakan package manager

Di distro turunan debian:
```
sudo apt-get install openssh
```
Di distro turunan RHEL
```
sudo dnf install openssh
```
Di openSUSE
```
sudo zypper in openssh
```
Di distro turunan Arch
```
sudo pacman -S openssh
```
Distro lain menyesuaikan

## Syarat menjadi server SSH

* Komputer yang akan di remote harus mengaktifkan ssh

    Untuk yang menggunakan systemd
    ```
    sudo systemctl start sshd
    ```
    Untuk yang menggunaan sysVinit
    ```
    sudo service sshd start
    ```
    Untuk yang menggunakan init.d
    ```
    sudo /etc/init.d/sshd start
    ```
* Harus mengetahui `hostname` dan `alamat ip` komputer yang akan di remote

    Untuk mengetahui hostname
    ```
    hostname
    ```
    Untuk mengetahui alamat ip
    ```
    ip a
    ```
* Jika komputer yang akan di remote memiliki kata sandi maka harus tahu kata sandinya

## Cara Menggunakan SSH
Komputer yang akan meremote komputer lain istilahnya `client`. Jika anda menggunakan os `unix-like` maka langsung bisa dilakukan lewat `terminal` tetapi jika anda menggunakan windows, anda harus menggunakan aplikasi seperti `putty` dan jika anda menggunakan android maka anda harus install `termux`.

Setelah kita memenuhi syarat berikut
```
hostname, alamat ip, kata sandi (optional)
```
Maka cara melakukan ssh cukup sederhana
```
ssh hostname@a.l.a.m.a.t.i.p
```
Jika komputer yang akan di remote berada pada port tertentu misalnya android menggunakan port 8022
```
ssh hostname@a.l.a.m.a.t.i.p -p 8022
```

kemudian jika ada pertanyaan dijawab
```
yes
```
kemudian jika ada kata sandi ya masukkan kata sandi dan jika tidak ada ya otomatis masuk