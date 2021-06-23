---
layout: post
---
![samba](/assets/IMG/Screenshot_2021-05-30_19-45-04.png)

* Do not remove this line (it will not be displayed) 
{:toc}

## Download samba
`sudo pacman -S samba`
## Buat file smb.conf
Buka link [smb.conf](https://git.samba.org/samba.git/?p=samba.git;a=blob_plain;f=examples/smb.conf.default;hb=HEAD) kemudian salin seluruh codenya
## Letakkan file smb.conf di /etc/samba/
## Proses konfigurasi file smb.conf
### Sesuaikan isi smb.conf seperti berikut ini:
`workgrup = WORKGRUP`

`log file = /var/log/samba/%m.log`

### Buat konfigurasi sharing sesuai keinginan, contohnya yang paling sederhana:

    [sharing]
    comment = file sharing
    path = /home/namaku/Public
    browseable = yes
    read only = no
    guest ok = yes


## Pengaturan firewall
### Izinkan CIFS dengan perintah
`sudo ufw allow CIFS`
### Buat file /etc/ufw/applications.d/samba dan tempelkan kode berikut

    [Samba]
    title=LanManager-like file and printer server for Unix
    description=The Samba software suite is a collection of programs that implements the SMB/CIFS protocol for unix systems, allowing you to serve files and printers to Windows, NT, OS/2 and DOS clients. This protocol is sometimes also referred to as the LanManager or NetBIOS protocol.
    ports=137,138/udp|139,445/tcp


### Izinkan samba dengan perintah
`sudo ufw allow samba`
## Jalankan samba
`sudo systemctl start smb`
## Pastikan statusnya aktif
`sudo systemctl status smb`

[sumber](https://wiki.archlinux.org/title/Samba)

[back](./index.md)