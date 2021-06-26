---
layout: post
---

* blablalba
{:toc}

# Preparation
Jalankan `apache` dan `mariaDB`

# Download
[link Download](https://www.mediawiki.org/wiki/Download)

# Extract
```
tar zxfv mediawiki-1.36.1.tar.gz
```

# Pindah
```
sudo mv mediawiki-1.36.1 /srv/www/ht-docs
```

# Kepemilikan
```
sudo chown root:root mediawiki-1.36.1
```

# Rename
```
sudo mv mediawiki-1.36.1 mediawiki
```

# Buka Browser
```
localhost/mediawiki/api.php
```
hasil

![hasil](/assets/IMG/Screenshot_20210626_102318.png)

# Setup
klik `setup the wiki`

jika error

![error](/assets/IMG/wikierror.png)

silahkan install
```
sudo zypper in php7-fileinfo && sudo zypper in php7-intl
```
Hasil

![hasil](/assets/IMG/Screenshot_20210626_103423.png)

klik `Continue`

![hasil](/assets/IMG/Screenshot_20210626_103549.png)

klik `Continue` lagi

![hasil](/assets/IMG/Screenshot_20210626_103734.png)

Centang `mariaDB`

Database host `localhost`

Datebase name `namaku_wiki`

Datebase table prefix `tabelku`

Database username dan password `isi sendiri` sesuai akun anda

Kemudian seperti ini

![pilihan 1](/assets/IMG/pilihan1.png)

Jika anda ingin menggunakan akun tadi (root) untuk keperluan wiki silahkan klik `Continue`

Tetapi jika ingin menggunakan akun khusus untuk keperluan wiki maka jangan di centang biru, maka tampilannya seperti ini

![pilihan 2](/assets/IMG/pilihan2.png)

Silahkan membuat akun database khusus untuk keperluan wiki kemudian centang dan klik `Continue`

Langkah selanjutnya isi sesuka hati

![](/assets/IMG/Screenshot_20210626_105225.png)

Perhatikan bahwa Administrator account yang ini berbeda dengan yang tadi, yang tadi itu akun untuk akses database mysql sedangkah yang ini akun untuk halaman wiki

Langkah selanjutnya silahkan diikuti saja

![lanjut](/assets/IMG/Screenshot_20210626_105718.png)

# Install
![](/assets/IMG/Screenshot_20210626_110256.png)

klik `continue` untuk memulai proses installasi

![](/assets/IMG/Screenshot_20210626_110423.png)

Klik `Continue` lagi

![](/assets/IMG/Screenshot_20210626_110531.png)

Oke, Berhasil!

Silahkan di save file tersebut dan pindahkan ke directory mediawiki
```
sudo mv Downloads/LocalSettings.php /srv/www/htdocs/mediawiki    
```

# Mulai menulis
setelah file `LocalSettings.php` diletakkan di directory mediawiki, klik `enter your wiki`

![](/assets/IMG/Screenshot_20210626_111203.png)

Selamat berkarya!