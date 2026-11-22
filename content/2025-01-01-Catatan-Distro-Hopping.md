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

# Ubuntu
+ Dokumentasi cukup lengkap (karena sering digunakan oleh beginner)
+ Dukungan aplikasi No 1
- Ndak keren, include cannonical
- sekarang ubuntu server live, tidak ada netinstall
- iso ubuntu (xubuntu, lubuntu, ubuntu mate dkk, pop-os (BIOS), ubuntu server) diatas 2GB semua sehingga harus menyiapkan bootable minimal 8GB. iso rubuntu (EFI) dan linux lite (EFI) masih bisa menggunakan bootable 4GB.

# Arch
+ Keren
+ Stabil (pake kernel lts)
+ Full Custom
+ AUR memungkinkan dukungan aplikasi sebanyak Ubuntu bahkan lebih
+ Dokumentasi wiki.arhlinux.org lengkap
+ Bagus untuk orang gabut, seneng ngoprek, pengin tahu daleman OS
+ Software terbaru
+ Bisa BIOS atau EFI
- Menyita waktu
- Ngonfig dari 0

# Fedora
+ Dokumentasi lengkap
+ Komunitas oke
+ Desktop oke
- Default pake EFI
- Ndak stabil karena bukan Linux-LTS
- Default pake keyring
- Pake Flatpak
- Harus ngonfig codecs audio, epel, rpm free non-free

# Rocky
+ Stabil
- Tidak selengkap fedora
- Dan beda dengan fedora
- Troubleshoot kurang
- Codecs ffmpeg ada yg ndak bisa ketika pake audacity
- Terus ketika install FFmpeg dan running audacity masih error, alasannya ffmpeg tidak ikut terinstall ketika menginstall audacity, audacity direinstall, seluruh cache dan konfigurasi audaciy yg terinstall sudah diremove masih tetap

# RHEL
- ribet kurang fleksibel, secure bgt sampe pusing mau ngp-ngp dibatasi security
- usb habis nginstall rhel ada iso9660 yg bikin pusing. solusinya pake [cara ini](./_posts/2025-01-01-Creating-Bootable.md)

# Docker
+ Bisa install ubuntu, rocky, alpine, dan linux-linux lain tanpa virtualisasi tapi cuma shell

# Recommended
+ install linux-lts terus coba-coba pake virtualbox berbagai distro sampe nemu yg cocok
