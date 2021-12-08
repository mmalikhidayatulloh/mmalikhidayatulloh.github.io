# Pengaturan Xinit
1. Copy konfigurasi ke home directory
    ```
    cp /etc/X11/xinit/xinitrc .xinitrc
    ```
2. Beri tanda # supaya konfigurasi tidak dijalankan system
    ```
    #twm &
    # xclock -geometry 50x50-1+1 &
    # xterm -geometry 80x50+494+51 &
    # xterm -geometry 80x20+494-0 &
    # exec xterm -geometry 80x66+0+0 -name login
    ```
3. Masukkan konfigurasi sesuai keinginan
    ```
    # Compositor
    
    picom -f &
    nitrogen --restore &
    
    # execute DWM
    
    exec dwm
    ```
4. Jalankan
    ```
    startx
    ```
Pengaturan touchpad
1. Install 
    ```
    sudo pacman -S xf86-input-synaptics
    ```
2. 