---
layout: post
---

* Do not remove this line (it will not be displayed) 
{:toc}

# Pendahuluan
* Pastikan bahwa `apache` maupun `nginx` sudah terinstall di komputer anda.
* Untuk mengedit file `/etc/` anda harus menjadi `super user/root` atau menggunakan `sudo`

# Apache
## Edit file /etc/apache2/default-server.conf
Fokus pada kalimat ini dan sesuaikan dengan folder yang akan anda tampilkan di web
```
DocumentRoot "/srv/www/htdocs"
<Directory "/srv/www/htdocs">
Options None
```
Misalnya ingin menampilkan directory `/home/malik/Documents/`maka konfigurasi di atas menjadi

```
DocumentRoot "/home/malik/Documents/"
<Directory "/home/malik/Documents">
Options All
```
Sesuaikan dengan keinginan Anda, dan jangan lupa untuk mengganti `Options none` menjadi `Options All` agar semua file dapat ditampilkan, tidak hanya file `index.html` saja
## Restart Apache
```
sudo systemctl restart Apache2
```
## Hasil
![](/assets/IMG/Screenshot_20210618_232056.png)

# Nginx
## Edit file /etc/nginx/nginx.conf
fokus pada kalimat berikut
```
location / {
        root   /srv/www/htdocs/;
        
        index  index.html index.htm;
        }
```
Ganti sesuai alamat directory yang akan ditampilkan di website.

Misalnya saya akan menampilkan `/home/malik/Documents` maka kalimat di atas saya ganti menjadi
```
location / {
        root   /home/malik/Documents/library/;
        autoindex on;
        }
```
Perhatikan bahwa ada kalimat `autoindex on;` menggantikan `index  index.html index.htm;` agar seluruh isi directory ditampilkan ke website
## Restart nginx
```
sudo systemctl restart nginx
```
## Hasil
![](/assets/IMG/Screenshot_20210618_232353.png)