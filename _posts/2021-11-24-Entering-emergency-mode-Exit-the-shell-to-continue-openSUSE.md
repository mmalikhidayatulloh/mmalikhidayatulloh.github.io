Hal ini terjadi ketika baterai saya rusak, harus make charge jika ingin digunakan. Jadi ketika saya cabut chargernya laptop langsung off mendadak. dan ketika dihidupkan kembali muncul seperti ini

```
"Entering emergency mode. Exit the shell to continue."
Type "journalctl" to view system logs.
You might want to save "/run/initramfs/rdsosreport.txt" to a usb stick or
/boot after mounting them and attach it to a bug report. 
```

Tentu saya agak panik, tapi untungnya saya masih megang HP dan hal pertama yang saya lakukan setelah membaca error tersebut adalah mencoba memasukkan kata sandi root, tetapi setelah itu bingung mau ngapain, terus di error tersebut ada kalimat "Ctrl - D" dan ketika saya lakukan ternyata cuma exit dari root. Setelah itu saya reboot laptop saya. dan lanjut browsing.

Ternyata masalah ini sudah ada solusinya tetapi untuk distro CentOS, sedangkan distro yang saya gunakan adalah openSUSE. Solusi yang diberikan untuk CentOS saya coba terapkan, dalam website yang saya baca solusinya seperti ini

```
xfs_repair -v -L /dev/dm-0
xfs_repair -v -L /dev/dm125
xfs_repair -v -L /dev/dm126
xfs_repair -v -L /dev/dm127
```

tetapi ketika saya masukkan command tersebut yang keluar adalah `tidak ada commad xfs`. Oke, lumayan panik sedikit.

Karena belum solved, maka saya reboot lagi dan browsing lagi, setelah saya baca-baca beberapa website. Alhamdulillah ternyata solusinya cukup mudah. Cukup masuk ke root kemudian masukkan command 

```
fsck -y /dev/sda1
```

solusi ini saya dapat dari website [ini](https://bobcares.com/blog/welcome-to-emergency-mode-in-linux-boot-error/   )