flatpak, snap, Appimage termasuk universal packaging artinya bisa digunakan di semua distro linux. Ada kalanya ketika kita ingin menginstall package tertentu tetapi package tersebut tidak tersedia di repository official dari distro linux yang kita miliki. Untuk mengatasi masalah ini maka kita bisa menggunakan flatpak atau snap atau AppImage.

## 1. Mencari package

```
$ flatpak search <nama package>
```

## 2. Menginstall package

```
$ flatpak install <nama package>
```

## 3. Uninstall package

```
$ flatpak uninstall <nama package>
```

## 4. Uninstall package yang tidak dibutuhkan

```
$ flatpak uninstall --unused
```

## 5. Setup flatpak

```
$ flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo
```

## 6. Bantuan

```
$ flatpak --help
```

## 7. Menampilkan daftar package yang terinstall

```
$ flatpak list
```