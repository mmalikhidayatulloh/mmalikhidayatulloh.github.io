1. Ikuti langkah pengaturan `.xinitrc`
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