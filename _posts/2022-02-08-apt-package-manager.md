# Install, hapus dan upgrade packages
* Install package:
```
apt install <package>
```
* Reinstall package:
```
apt reinstall <package>
```
* Reinstall package dan semua dependencinya
```
apt reinstall <package> $(apt-cache depends --recurse --installed <package> ||grep '[ ]')
```
* Hapus package:
```
apt remove <package>
```
* Hapus package and semua configurasinya dan data file (Perhatikan)
```
apt purge <package>
```
* Upgrade Package:
```
apt upgrade <package>
```
* upgrade semua package tanpa menghapus apapun (upgrade aman):
```
apt update
apt upgrade
```
* To menjalankan package upgrade yang perlu untuk menginstall atau menghapus beberapa package lain
```
apt dist-upgrade
```
# Mencari packages
* ganti <string> dengan daftar kata kunci untuk mencari (dalam nama package atau descripsinya).
```
apt search <string>
```
* untuk mencari hanya nama packagenya saja
```
dpkg-query -l '*<string>*'
```
* mencari informasi package dalam directory berikut:
```
/var/lib/apt/lists/*
```
* daftar package yang tersedia dari repositori
```
/var/lib/dpkg/available
```
* status package yang terinstall dan tersedia. file ini butuh informasi tentang apakah sebuah package ditandai untuk dihapus atau tidak, apakah terinstall atau tidak, dll. package yang ditandai reinst-required artinya rusak dan perlu untuk diinstall ulang.
```
/var/lib/dpkg/status
```
# apt-file
* mencari nama file: untuk mencari package yang menyediakan sebuah nama file tertentu
```
apt-file search <filename>
```
* daftar konten package: tanpa butuh untuk menginstall atau mendownloadnya
```
apt-file list <packagename>
```
* Update database package: update informasi database package
```
apt-file update
```
# Daftar package yang terinstall
```
dpkg --list 
aptitude search ~i 
dpkg-query -l 
dpkg-query -f '${binary:Package}\n' -W 
dpkg -l | grep '^.i' 
apt-cache pkgnames 
dpkg --get-selections
```
* Untuk mengecek status dari package yang terinstall
```
dpkg-query -l '*' | less
```
# daftar file yang diinstall oleh package
```
dpkg -L <package>
```
# hapus cache file package
APT memelihara cache lokal dari downloaded/installed .deb packages di `/var/lib/apt/cache/`. jika anda ingin menghapus file cache package yang sudah anda install to mendapatkan kembali beberapa ruang penyimpanan
```
apt clean
```
jika anda ingin mempertahankan cache lokal hanya untuk versi saat ini
```
apt autoclean
```
# konfigurasi ulang packages
```
dpkg-reconfigure <package>
```
# Temukan paket apa yang dimiliki file
```
dpkg -S /path/to/file
```
# Temukan paket mana yang bergantung pada paket tertentu
```
apt-cache rdepends mypackage
```