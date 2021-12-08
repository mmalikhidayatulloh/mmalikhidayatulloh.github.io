1. Ikuti langkah pengaturan `.xinitrc` terutama penambahan
    ```
    exec dwm
    ```
2. Jangan lupa install peralatan untuk compile
    ```
    sudo pacman -S base-devel linux-headers
    ```

3. clone repository
    ```
    git clone https://git.suckless.org/dwm
    git clone https://git.suckless.org/dwmstatus
    git clone https://git.suckless.org/st
    git clone https://git.suckless.org/slock
    ```
4. Compile masing-masing package
    ```
    make
    sudo make install
    ```
5. Jalankan
    ```
    startx
    ```
6. Untuk keluar dari window manager
    ```
    alt + shift + q
    ```
7. Memasang patches dengan cara biasa

    Patches di sini seperti tambahan-tambahan atau plugin atau add-ins. Tersedia di website [ini](https://dwm.suckless.org/patches/)

    Pilih patch yang diinginkan, misalnya `dwm-fullgaps`.

    Download filenya dan taruh di directory `dwm`

    ```
    wget https://dwm.suckless.org/patches/fullgaps/dwm-fullgaps-6.2.diff
    ```

    ```
    patch < dwm-fullgaps-6.2.diff
    sudo cp config.deff.h config.h
    sudo make install
    ```
    ada dua versi dwm-fullgaps. Jika salah satu tidak bekerja maka gunakan versi yang satunya lagi.

    hal yang sama untuk patch yang lain.

8. Ganti tombol `mod`

    Secara default modnya menggunakan tombol `alt` yaitu `mod1` di dalam file `config.def.h` dan `config.h`.

    Untuk mengganti menjadi tombol `windows` maka `mod1` dirubah menjadi `mod4` kemudian di compile ulang dan di refresh.