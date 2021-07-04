---
layout: post
---
* toc
{:toc}

Virtualisasi merupakan salah satu cara agar bisa menjalankan OS di dalam OS, misalnya linux di dalam windows maupun sebaliknya, bisa juga windows di dalam macOS. selain itu virtualisasi juga merupakan cara yang aman untuk mencoba-coba/simulasi atau istilah kasarnya `ngoprek`. Ada banyak software yang digunakan untuk virtualisasi, misalnya `virtual-box`, `VM Ware`, `QEMU/KVM`, `XEN`, `Virtul Machine Manager`. Dalam distro `openSUSE` sudah tersedia fitur `Virtualisasi` di `YaST`. Virtualisasi yang disediakan adalah `Xen` dan `QEMU/KVM`. Untuk mengaktifkannya cukup mudah.

# 1. Installasi
Buka `YaST` pilih `Software Management`, pada pattern centang `KVM Host Server` jika ingin menggunakan `QEMU/KVM` atau `Xen Virtual Machine Host Server` jika ingin menggunakan `Xen`. Centang juga `KVM Virtualization Host and Tools` maupun `Xen Virtualization Host and Tools`.

Setelah di unduh, Kemudian buka `YaST` pilih menu `Virtualization` dan pilih `Install Hypervisor and tools` kemudian centang pada `KVM Server` dan `KVM Tools` maupun `Xen Server` dan `Xen Tools`.
# 2. Penggunaan
Pastikan `libvirtd` sudah aktif, cara mengaktifkannya bisa menggunakan
```
# systemctl start libvirtd
```

Kemudian `Create Virtual Machines`

Install OS Seperti biasa. Misalnya saya seperti ini:

Pilih `Local install media(ISO image or CDROM)` kemudian `Forward
`

Klik `Browse...` kemudian `Browse Local` dan arahkan ke file `.iso`

Pada `choose the operating system you are installing`, pilih jenis OS kemudian `Forward`

Atur memory/RAM dan CPU kemudian `Forward`

Atur Penyimpanan Internal kemudian `Forward`

Pada `Network Selection` defaultnya menggunakan `NAT`, jika ingin mode `bridge` maka anda perlu mengecek host OS anda seperti berikut
```
ifconfig
```

Hasilnya

![ifconfig](/assets/IMG/Screenshot_20210705_043902.png)

Dari hasil di atas terdapat tulisan `virbr0` yang merupakan nama bridge-nya

Masuk lagi pada proses installasi VM.

Pada `Network selection` pilih `bridge device` dan masukkan `virbr0` pada device name. Kemudian klik `Finish`

Secara otomatis masuk ke installasi OS di Virtual Machine, biasanya halamannya langsung menghilang dari layar, tapi jangan khawatir karena prosesnya tetap berjalan cuma layarnya saja yang ditutup. Untuk melanjutkan installasi OS nya silahkan buka `Applications menu` pada host OS anda dan buka applikasi `Virtual Machine Manager` nanti anda akan menemukan bahwa OS yang akan anda install dalam keadaan running. untuk melanjutkan proses installasi OS silahkan klik `Open`

Lakukan Installasi OS seperti biasa
