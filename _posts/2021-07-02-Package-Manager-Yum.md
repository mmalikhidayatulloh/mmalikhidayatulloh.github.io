---
layout: post
---

* toc
{:toc}

Panduan ini saya buat ketika saya menginstall centos versi 7. Ketika saya mengguanakan `dnf` ternyata centos mengatakan bahwa tidak ada package dnf, padahal di pikiran saya tahunya kalo distro berbasis redHat menggunakan package manager dnf, tetapi kali ini berbeda karena centos 7 masih menggunkan kernel 3 dan ketika panduan ini dibuat kernel terbaru sudah kernel 5.13. tetapi dukungan untuk centos 7 masih sampai 2024 sedangkan centos 8 hanya sampai 2021. Package manager yang digunakan oleh centos 7 adalah `yum`.

Perlu diketahui bahwa konfigurasi utama yum berada di `/etc/yum.conf` dan konfigurasi terkait repository `/etc/yum.repos.d`. Beberapa perintah dasar yum:

# 1. Untuk list/melihat daftar repository
```
# yum repolist
```
# 2. Untuk melihat daftar package yang tersedia berdasarkan keyword tertentu
misalnya dengan keyword `yum`
```
# yum list 'yum*'
```
# 3. Untuk melihat daftar package yang terinstall
```
# yum list installed
```
# 4. Untuk melihat package-group yang tersedia
```
# yum grouplist
```
# 5. Untuk menampilkan cara menggunakan yum
```
# yum help
```
# 6. Untuk mencari package
```
# yum search
```
# 7. untuk mengetahui informasi package
```
# yum info
```
# 8. Untuk mengetahui diretory yang berhubungan dengan package
```
# yum provide /var/www/html
```
# 9. Install package
```
# yum install
```
y : untuk install
d : untuk download tetapi tidak diinstall
n : untuk batal
# 10. Remove package
```
# yum remove
```
# 11. Update seluruh package
```
# yum update
```
update secara spesifik
```
# yum update NAMAPACKAGE
```
update kernel
```
# yum update kernel
```
# 12. Menampilkan informasi grup
```
# yum group info
```
tanda = Package terinstall melalui grup

tanda + package tidak terinstal tapi akan di install atau diupdate

tanda - package terinstall tetapi bukan melalui grup 

tanpa tanda package tidak terinstall dan tidak akan diinstall melalui grup
# 13. Install grup
```
# yum group install "Infiniband Support"
```
# 14. Menampilakan log yum
```
tail -5 /var/log/yum.log
```
# 15. Untuk melihat history yum
```
# yum history
```
# 16. enable dan disable repository
```
# yum-config-manager --enable NAMAREPOSITORY
```
# 17. Menambah repository
Cara 1:Bisa langsung diisi ke `/etc/yum.repos.d` masukkan url dan nama serta GPG Key
```
# yum-config-manager --add-repo="urlrepository"
```
ganti baris `enable=` menjadi `enable=1` supaya repository bisa digunakan
