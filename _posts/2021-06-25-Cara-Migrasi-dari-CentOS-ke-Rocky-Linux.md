---
layout: post
---
![rocky](/assets/IMG/rocky.png)

* Do not remove this line (it will not be displayed) 
{:toc}

Setelah adanya berita dari RedHat bahwa centos tidak akan dilanjutkan kembali setelah desember 2021 dan akan dialihkan ke centos stream maka user centos banyak yang kecewa dengan keputusan ini sehinnga beberapa user ada yang mulai migrasi ke debian maupun openSUSE dan developer ada yang membuat gerakan untuk mengatasi kekecewaan tersebut dengan membuat distro linux yang baru yang kompatibel dengan RedHat, diawali oleh Alma Linux yang langsung launching tidak lama setelah adanya kebijakan baru RedHat tersebut. Kemudian di belahan dunia yang lain sebuah project distro linux pengganti Centos didirikan oleh seseorang yang dulunya pernah menjadi pendiri centos, projectnya bernama `Rocky linux`. Pada bulan juni 2021 rocky linux rilis untuk pertama kalinya dan di sini saya akan mencoba mendemonstrasikan cara untuk migrasi dari Centos ke Rocky linux.

# 1. Pastikan CentOS dalam kondisi update
```
sudo dnf update && sudo dnf upgrade
```
# 2. Migrasi
* Downlod script untuk migrasi ke Rocky linux
```
curl -O https://raw.githubusercontent.com/rocky-linux/rocky-tools/main/migrate2rocky/migrate2rocky.sh
```
* Edit Hak Akses Agar Bisa dijalankan
```
sudo chmod +x migrate2rocky.sh
```
* Jalankan script migrasinya
```
sudo ./migrate2rocky.sh -r
```
>Penjelasan
```
./migrate2rocky.sh -h
├── -h   # --> Display this help
├── -r   # --> Convert to Rocky
└── -V   # --> Verify switch
```
* Outputnya seperti ini
  
  [proses]()
# 3. Update
```
sudo dnf distro-sync -y 
```
4. Reboot
```
sudo reboot
```
5. Cek
```
cat /etc/os-release
```
```
cat /etc/redhat-release
```
# Sumber

[https://ostechnix.com/how-to-migrate-to-rocky-linux-8-from-centos-8-linux/](https://ostechnix.com/how-to-migrate-to-rocky-linux-8-from-centos-8-linux/)

[https://github.com/rocky-linux/rocky-tools/tree/main/migrate2rocky](https://github.com/rocky-linux/rocky-tools/tree/main/migrate2rocky)