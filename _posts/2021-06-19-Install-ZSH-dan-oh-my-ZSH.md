---
layout: post
---

* Do not remove this line (it will not be displayed)
{:toc}

Zsh merupakan salah satu jenis shell yang digunakan di perangkat linux, bsd, maupun macos. Karena OS tersebut menyediakan terminal dan untuk berinteraksi dengan terminal menggunakan shell, selain Zsh ada beberapa shell lain seperti sh, ksh, fish, dan yang paling sering dijumpai di linux adalah Bash. Zsh merupakah shell yang interaktif karena adanya kemudahan untuk dicustomisasi dengan plugin yang cukup banyak. Bahkan salah satu distro linux turunan Arch linux yang bernama manjaro menggunakan zsh sebagai shell defaultnya.

# Install Zsh
Zsh bisa diinstall dengan package manager, sesuaikan dengan jenis OS yang anda gunakan, misalnya:

Di openSUSE:
```
sudo zypper in zsh
``` 
Di debian:
```
sudo apt install zsh
```
Di Arch linux:
```
sudo pacman -S zsh
```
Di redHat:
```
sudo dnf install zsh
```
# Masuk ke Zsh
```
zsh
```
Keluar dari zsh
```
exit
```
# Install oh-my-zsh
## Install oh-my-zsh menggunakan curl
pastikan `curl` sudah terinstal di perangkat Anda
```
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
## Install oh-my-zsh menggunakan wget
pastikan `wget` sudah terinstall di perangkat Anda
```
sh -c "$(wget https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh -O -)"
```
# Memilih tema
Masuk ke `.zshrc`
```
vim .zshrc
```
Edit bagian `ZSH_THEME=""` sesuai tema yang tersedia, misalnya `agnoster`
```
ZSH_THEME="agnoster"
```
Pilihan tema tersedia di [https://github.com/ohmyzsh/ohmyzsh/wiki/Themes](https://github.com/ohmyzsh/ohmyzsh/wiki/Themes)
# Memilih plugin
Beberapa plugin favorit saya:
## Zsh-syntax-highlighting
clone repository
```
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```
Edit `.zshrc`
```
plugins=( pluginlain zsh-syntax-highlighting)
```
## Zsh-autosuggestions
Clone repository
```
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
```
Edit `.zshrc`
```
plugins=( pluginlain zsh-autosuggestions)
```
# Menerapkan konfigurasi
```
source .zshrc
```


# Sumber
[oh-my-zsh](https://ohmyz.sh/)

[zsh-autosuggestion](https://github.com/zsh-users/zsh-autosuggestions/blob/master/INSTALL.md)

[zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting/blob/master/INSTALL.md)