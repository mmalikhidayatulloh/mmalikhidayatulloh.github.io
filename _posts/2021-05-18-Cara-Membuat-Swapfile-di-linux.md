---
layout: post
---
* Do not remove this line (it will not be displayed) 
{:toc}

Linux divides its physical RAM (random access memory) into chunks of memory called pages. Swapping is the process whereby a page of memory is copied to the preconfigured space on the hard disk, called swap space, to free up that page of memory. The combined sizes of the physical memory and the swap space is the amount of virtual memory available.

As an alternative to creating an entire partition, a swap file offers the ability to vary its size on-the-fly, and is more easily removed altogether. This may be especially desirable if disk space is at a premium (e.g. a modestly-sized SSD)

### Buka terminal
### Login sebagai root/super-user
```
su
```
### Masuk ke direktory root
```
$ cd /
```
### Buat swapfile
```
dd if=/dev/zero of=/swapfile bs=1M count=2048 status=progress
```
### Atur permission swapfile
```
chmod 600 /swapfile
```
### Aktifkan swapfile
```
mkswap /swapfile
```
### Backup /etc/fstab
```
cp /etc/fstab /etc/fstab.backup
```
### Tambahkan konfigurasi swapfile ke /etc/fstab
```
echo '/swapfile none swap sw 0 0' | tee -a /etc/fstab
```
### cek /etc/fstab
```
cat /etc/fstab
```
### Aktifkan
```
# mount -a
# swapon -a
```