---
layout: post
---
* Do not remove this line (it will not be displayed) 
{:toc}

Terminal sangat-sangat usefull di perangkat unix-like, hampir seluruh hal yang dibutuhkan bisa dilakukan menggunankan terminal, maka tidak heran jika sebuah server tidak membutuhkan `GUI` karena cukup dengan `CLI` semua bisa dilakukan. Salah satunya adalah connect ke jaringan. Misalnya `wifi`.

Untuk connect ke wifi menggunakan terminal caranya sebagai berikut:
# 1. Cek Wifi yang tersedia
```
nmcli d wifi list
```
# 2. Connect ke wifi yang tersedia
misalnya tersedia wifi dengan nama "Redmi 5A"
```
nmcli d wifi connect Redmi\ 5A
```
# 3. Cek apakah sudah terhubung
```
ifconfig
```
Jika terhubung pasti ada `ip address`