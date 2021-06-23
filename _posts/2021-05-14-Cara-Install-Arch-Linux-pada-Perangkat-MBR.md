---
layout: post
---
![](https://roboticoverlords.org/wallpapers/simple.png)

* Do not remove this line (it will not be displayed) 
{:toc}

A simple, lightweight distribution
Arch Linux is an independently developed, x86-64 general-purpose GNU/Linux distribution that strives to provide the latest stable versions of most software by following a rolling-release model. The default installation is a minimal base system, configured by the user to only add what is purposely required. 


1. Download file .iso Arch linux dari [website resmi Arch](https://archlinux.org) klik menu `Download`, scroll ke bawah cari mirror untuk Indonesia, klik link mirrornya, download file `archlinux-version-x86_64.iso` dan file `archlinux-version-x86_64.iso.sig`
2. Verifikasi file .iso yang telah di download dengan cara

       $ pacman-key -v archlinux-version-x86_64.iso.sig


    nanti akan keluar seperti ini

       ==> Checking archlinux-2021.05.01-x86_64.iso.sig... (detached)
       gpg: Signature made Sab 01 Mei 2021 12:24:14  WIB
       gpg: using RSA key 4AA4767BBC9C4B1D18AE28B77F2D434B9741E8AC
       gpg: Note: trustdb not writable
       gpg: Good signature from "Pierre Schmitz <pierre@archlinux.de>" [full]


3.  Kemudian buat usb bootable
>Banyak cara untuk membuat usb bootable, di windows bisa pake rufus, di linux bisa pake terminal dengan perintah `dd if=/directoryfileiso of=/directoryUSB`, atau bisa juga menggunakan balena etcher yang support di berbagai os

4. Pastikan settingan di BIOS bahwa priotitas bootnya adalah usb
Ketika laptop baru menyala, tekan F2 sampai masuk ke menu BIOS kemudian cari menu boot dan atur usb agar berada di paling atas
5. Shutdown laptop dan Pasang usb bootable kemudian nyalakan laptop
6. Klik install Arch linux
7. Setelah itu masuk ke mode installasi Arch linux, tampilannya full Command Line Interfaces
8. Cek apakah sudah terhubung ke Internet, bisa dengan `ping` atau `ifconfig`
9. Jika belum maka wajib hukumnya connect ke internet.

   Jika menggunakan wifi:
   
   Masukkan perintah `iwctl`
   
   Kemudian `station wlan0 connect "Nama wifinya"`

   Kemudian `exit`

   Cara lainnya dengan perintah `wifi-menu` cara ini lebih mudah untuk pemula

10. Set keyboard dengan cara

    `loadkeys us`

11. Set waktu dengan

    `timedatectl set-ntp true`

12. Cek penyimpanan dengan perintah

    `lsblk`

13. Mulai atur partisi
    
    >Langkah ini paling beresiko!
    
    Jalankan perintah `fdisk /dev/sda`
    
    Klik `n` untuk partisi baru
    
    Klik `p` untuk primary (partisi utama)

    Klik `enter` untuk partitions number sebagai default yaitu 1

    Klik `enter` untuk First sector (sesuai default)

    Jika ingin full partisi langsung klik enter (untuk swap urusan gampang karena bisa pake `swapfile`)

    Jika ingin swap terpisah, Klik `n` kemudian `p` kemudian `enter` kemudian `enter` lagi kemudian `+2G` (untuk swap 2GB)

    Klik `w` untuk menyimpan pengaturan

14. Cek lagi dengan `lsblk`
15. Jika menggunakan swap terpisah maka perlu mengaktifkan swap dengan cara `mkswap /dev/sda1` atau sda2 sesuai lokasinya. kemudian `swapon /directorySWAPnya`
16. Setelah itu format untuk partisi rootnya dengan  `mkfs.ext4 /dev/sda2` atau sda1 sesuai lokasinya
17. Kemudian partisi rootnya di mount dengan cara

        mount /dev/sda2 /mnt

18. Kemudian install package linux dasar ke /mnt

        pacstrap /mnt base base-devel linux linux-firmware vim

19. Kemudian

        genfstab -U /mnt >> /mnt/etc/fstab

20. Cek fstab sudah terisi

        cat /mnt/etc/fstab

21. Kemudian

        Arch-chroot /mnt

22. Kemudian Setting zona waktu

        ln -sf /usr/share/zoneinfo/Asia/Jakarta /etc/localtime

23. Kemudian

        hwclock --systohc

24. Kemudian 

        vim /etc/locale.gen

    Hapus tanda # pada `# en_US.UTF-8`

25. Kemudian

        locale-gen

26. Kemudian

        vim /etc/locale.conf
    
    Masukkan `LANG=en_US.UTF-8`

27. Kemudian setting hostname

        vim /etc/hostname


    Masukkan nama hostname sesuai keinginan Anda. Misalnya `lenovo-K2180`
28. Kemudian

        vim /etc/hosts
    
    
    masukkan seperti berikut

        127.0.0.1   localhost
        ::1         localhost
        127.0.0.1   lenovo-K2180

29. Kemudian set root password

        passwd

30. Kemudian install package lain

        pacman -S grub networkmanager network-manager-applet wireless_tools wpa_supplicant dialog os-prober linux-headers mtools dosfstools 

31. Kemudian

        grub-install --target=i386-pc /dev/sda

32. Kemudian

        grub-mkconfig -o /boot/grub/grub.cfg

33. Kemudian

        systemctl enable NetworkManager

33. Kemudian

        exit

34. Kemudian

        umount -a

35. Lepas usb installer dan `reboot`

[back](./index.md)