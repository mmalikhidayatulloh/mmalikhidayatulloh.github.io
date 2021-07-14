---
layout: post
---

* toc
{:toc}

# 1. Installasi
Proses Installasinya saya menggunakan Virtual Machine, belum pernah di laptop secara langsung maupun dualboot. Prosesnya cukup mudah karena saya menggunakan konfigurasi versi otomatis.

# 2. Setelah Installasi
Centos 7 menggunakan package manager `yum` dan ternyata lebih mudah dibandingkan `dnf`

Tentu setiap selesai install linux saya selalu update dulu
```
yum update
```

Kemudian `reboot`

Dari segi kesediaan package masih lebih banyakan di dnf. karena ketika saya menggunakan yum tidak bisa install beberapa package favorit saya seperti `neofetch` dan `htop`. Maka untuk menginstall neofetch saya masih membutuhkan `dnf`:

```
yum install -y epel-release
yum install -y dnf
yum install -y dnf-plugins-core
dnf -y copr enable konimex/neofetch
dnf install -y neofetch
neofetch
```

untuk install `htop`
```
yum install htop
```
Pada proses installasi, saya membuat user dan secara default `user` yang saya buat pada saat proses installasi masuk dalam grup yang namanya sama dengan nama user. Untuk itu saya ingin membuat agar `user` yang saya buat tadi masuk ke dalam grup `wheel` dan grup `wheel` ini menjadi grup utamanya. Sehingga secara otomatis bisa menggunakan perintah `sudo`.
```
usermod -g whell username
```

Kemudian saya akan mengatur agar hanya user ini yang bisa beralih ke root menggunakan perintah su
```
vi /etc/pam.d/su
```

Hapus tanda `#` pada
```
auth    required    pam_wheel.so use_uid 
```

Seperti ini

![pam.d](/assets/IMG/Screenshot_20210705_050516.png)

Kemudian cek status `firewalld`
```
systemctl status firewalld
```

Secara default status `firewalld` active

Cek status `SELinux`
```
getenforce
```

Hasilnya
```
Enforcing
```

Artinya aktif dan Secara default `SELinux` memang aktif

Set `hostname`, secara default hostnamenya
```
localhost.localdomain
```

untuk menggantinya
```
hostnamectl set-hostname namahostnamebaru
```

Cek koneksi
```
nmcli d
```

Hasilnya
```
DEVICE  TYPE      STATE      CONNECTION 
eth0    ethernet  connected  eth0       
lo      loopback  unmanaged  --         
```

artinya terhubung ke `eth0`


set ip
```
nmcli c modify eth0 ipv4.addresses 192.168.0.100/24
```

set default gateway
```
nmcli c modify eth0 ipv4.gateway 192.168.0.1
```

set dns
```
nmcli c modify eth0 ipv4.dns 192.168.0.1
```

Kemudian untuk set ip static (auto untuk DHCP)
```
nmcli c modify eth0 ipv4.method manual
```

restart interfaces dan reload settings
```
nmcli c down eth0; nmcli c up eth0 
```