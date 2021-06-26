---
layout: post
---
* blablabla
{:toc}

Salah satu cara untuk sharing file antara android dengan linux selain menggunakan USB, bluetooth, samba, ftp. yaitu menggunakan `rsync`.
# Syarat
## Di android
* openssh
* nmap
* rsync
* set password
* Akses file manager
## Di linux
* openssh
* rsync
# Dari Android ke Linux
```
rsync -azv /alamatfile hostnamelinux@alamatIPlinux:/directorytujuandilinux
```
misalnya saya ingin share document file.pdf di folder whatsapp ke directory /home/malik/Document di linux
```
rsync -azv storage/shared/Whatsapp/Media/WhatsApp\ Documents/file.pdf malik@192.168.43.205:/home/malik/Documents
```
# Dari Linux ke Android
## Jalankan SSH di termux
```
sshd
```
## Cek port
```
nmap localhost
```
biasanya portnya 8022
## Lakukan rsync
```
rsync -azv -e 'ssh -p 8022' ./home/malik/Documents/file.pdf u0_a98@192.168.43.1:/data/data/com.termux/files/home/  
```