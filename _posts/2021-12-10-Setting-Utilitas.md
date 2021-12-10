# Install cups
```
sudo pacman -S cups
```
# Aktifkan cups
```
sudo systemctl start org.cups.cupsd.service
```
# Install hplip
```
sudo pacman -S hplip
```
# Install simple-scan
```
sudo pacman -S simple-scan
```
# Install bluetooth
```
sudo pacman -S bluez bluez-utils
```
# Run bluetooth
```
sudo systemctl start bluetooth
```
# Install ttf-ms-fonts
```
git clone https://aur.archlinux.org/ttf-ms-fonts.git
```
Compile
```
makepkg -si PKGBUILD
```