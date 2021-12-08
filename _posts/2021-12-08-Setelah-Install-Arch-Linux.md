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
# Pengaturan touchpad
1. Install 
    ```
    sudo pacman -S xf86-input-synaptics
    ```
2. Copy konfigurasi
    ```
    sudo cp /usr/share/X11/xorg.conf.d/70-synaptics.conf /etc/X11/xorg.conf.d/
    ```
3. Tambah pengaturan
    ```
    Section "InputClass"
    Identifier "touchpad"
    Driver "synaptics"
    MatchIsTouchpad "on"
        Option "TapButton1" "1"
        Option "TapButton2" "3"
        Option "TapButton3" "2"
        Option "VertEdgeScroll" "on"
        Option "VertTwoFingerScroll" "on"
        Option "HorizEdgeScroll" "on"
        Option "HorizTwoFingerScroll" "on"
        Option "CircularScrolling" "on"
        Option "CircScrollTrigger" "2"
        Option "EmulateTwoFingerMinZ" "40"
        Option "EmulateTwoFingerMinW" "8"
        Option "CoastingSpeed" "0"
        Option "FingerLow" "30"
        Option "FingerHigh" "50"
        Option "MaxTapTime" "125"
        ...
    EndSection
    ```
4. Restart xorg

# Pengaturan brightness

1. Install package
    ```
    sudo pacman -S xorg-xbacklight
    ```
2. Penggunaan
    ```
    xbacklight -set 50
    ```
