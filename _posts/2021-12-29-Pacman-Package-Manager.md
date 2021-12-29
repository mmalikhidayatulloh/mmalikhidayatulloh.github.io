Pacman adalah managemen paket dalam distro Arch linux. Dalam artikel ini akan dijelaskan beberapa perintah dasar dalam menggunakan pacman di Arch linux dan membandingankan dengan disto-distro lain
# Update repository
```
# pacman -Syy
```
> di debian dan turunannya menggunakan `apt-get update`

> di openSUSE menggunakan `zypper ref`

> di RedHat dan turunannya menggunakan `yum check-update` atau `dnf check-update`

> di freeBSD binary package menggunakan `pkg update` untuk port menggunakan `portsnap fetch update`

# Upgrade package
```
# pacman -Syu
```
> di debian dan turunannya menggunakan `apt-get upgrade` dan untuk upgrade ke versi terbaru menggunakan `apt-get dist-upgrade`

> di openSUSE menggunakan `zypper up` dan untuk full upgrade ke versi terbaru menggunakan `zypper dup`

> di RedHat dan turunannya menggunakan `yum upgrade` atau `dnf upgrade`

> di freeBSD menggunakan `pkg upgrade` atau jika menggunakan port maka `cd /usr/ports/ports-mgmt/portmaster && sudo make install && sudo portmaster -a`
# Mencari package
```
# pacman -Ss namapackage
```
> di debian dan turunannya menggunakan `apt-get search namapackage`

> di openSUSE menggunakan `zypper se namapackage`

> di RedHat dan turunannya menggunakan `yum search namapackage` atau `dnf search namapackage`

> di freeBSD menggunakan `pkg search -f namapackage` atau di port menggunakan `cd /usr/ports && make search name=package`
# Informasi package
```
# pacman -Si namapackage
```
> di debian dan turunannya `apt show namapackage`

> di openSUSE `zypper if namapackage`

> di RedHat dan turunannya `yum info namapackage` atau `dnf info namapackage`

> di freeBSD `pkg info namapackage` atau `cd /usr/ports/category/port && cat pkg-descr`
# Install Package
```
# pacman -S namapackage
```
> di debian dan turunannya `apt-get install namapackage`

> di openSUSE `zypper in namapackage`

> di RedHat dan turunannya `yum install namapackage` atau `dnf install namapackage`

> di freeBSD `pkg install namapackage` atau `cd /usr/ports/category/port && sudo make install`
# Install Package local
```
# pacman -U namapackage.pkg.tar.xz
```
> di debian dan turunannya `dpkg -i namapackage.deb`

> di openSUSE `zypper in namapackage.rpm`

> di RedHat dan turunannya `yum install namapackage.rpm` atau `dnf install namapackage.rpm`

> di freeBSD `pkg add namapackage.txz`
# Remove package
```
# pacman -R namapackage
```
remove beserta dependensi
```
# pacman -Rs namapackage
```
> di debian dan turunannya `apt-get remove namapackage` untuk uninstall package beserta dependensinya `apt purge namapackage`

> di openSUSE `zypper rm namapackage` atau `zypper rm -u namapackage` untuk remove package beserta dependensinya

> di RedHat dan turunannya `yum remove namapackage` atau `dnf erase namapackage`

> di freeBSD `pkg delete namapackage` dan untuk remove dependensi yang tidak dibutuhkan `pkg autoremove`. dan jika menggunakan port `cd /usr/ports/path_to_port && make deinstall`

# remove cache
```
# pacman -Sc
```
> di debian dan turunannya `apt clean` atau `apt autoclean`

> di openSUSE `zypper clean`

> di RedHat `dnf clean`

# Remove orphane package (package yang tidak digunakan)
```
# pacman -Qdtq | pacman -Rs -
```
> di debian dan turunannya `apt autoremove`

> di openSUSE `zypper packages --unneeded`

> di RedHat dan turunannya `dnf autoremove`

# edit repository (untuk menambah maupun menghapus repository)
```
# vim /etc/pacman.conf
```
> di debian dan turunannya `/etc/apt/sources.list`

> di openSUSE `/etc/zypp/repos.d/${REPO}.repo`

> di RedHat dan Turunannya `/etc/yum.repos.d/${REPO}.repo`