# Prequisitions:
- Backup Dokumen penting ke Telegram (freebsd dan linux bisa diinstall telegram)
- bootable usb (atau ventoy. Siapkan 2: 1 untuk coba-coba 1 lagi untuk utama)
- hp (untuk browsing ketika ada problem)
- koneksi internet lancar
- bare metal
- waktu
- CPU dan RAM (kalo mau mainan virtualisasi)

# Linux vs FreeBSD
## Linux
+ Desktop
+ Server
+ Driver
+ Aplikasi
+ Binari
+ Dotfile
+ Dokumentasi
+ Troubleshoot
+ Komunitas
- Langsung core, resikonya kalo ngonfig salah ngrusak OS
- Setiap distro aturan ngonfignya sendiri-sendiri, sehingga harus milih jati diri mau yang mana.
- Setiap distro punya istilah sendiri
## FreeBSD
+ Server
+ Berasa keren banget (karena tidak banyak yang bisa)
+ Secure
+ Core terisolasi, kesalahan konfig tidak mengganggu kernel core
- Dokumentasi
- Komunitas
- Kompatibilitas
- Driver
- Aplikasi
- Compile dari source lama banget (pernah sampe sehari) dan ndak dijamin berjalan
- Pake binary kadang error
- kernel module kadang error dan ndak tahu solusinya ex: bhyve ndak booting, volume ndak los plong, brightness, vbox.

# Ubuntu Based
+ Dokumentasi cukup lengkap (karena sering digunakan oleh beginner)
+ Dukungan aplikasi No 1
- Ndak keren, include cannonical
# Arch
+ Keren
+ Stabil (pake kernel lts)
+ Full Custom
+ AUR memungkinkan dukungan aplikasi sebanyak Ubuntu
+ Dokumentasi wiki.arhlinux.org lengkap
- Ngonfig dari 0
# Fedora
+ Dokumentasi lengkap
+ Komunitas oke
+ Desktop oke
- Default pake efi bukan BIOS/MBR
- Ndak stabil karena bukan Linux-LTS
- Default pake keyring
- Pake Flatpak
- Harus ngonfig codecs audio, epel, rpm free non-free
# Rocky
+ Stabil
- Tidak selengkap fedora
- Dan beda dengan fedora
- Troubleshoot kurang
- Codecs ffmpeg ada yg ndak bisa ketika pake audacity. 
