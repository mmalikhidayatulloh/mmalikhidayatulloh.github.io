Menggunakan Terminal
Cek dulu

df
Nama usb biasanya

/dev/sdb
Umount

sudo umount /dev/sdb

To format a USB drive with FAT32 file system, use:
sudo mkfs.vfat /dev/sdb
To format a USB drive using the NTFS file system run:
sudo mkfs.ntfs /dev/sdb
To format a USB drive in accordance with the exFAT file system use:
sudo mkfs.exfat /dev/sdb
Confirm the formatting process has completed successfully:

sudo fsck /dev/sdb
Hasil

~ >>> sudo fsck /dev/sdb                                                                        
fsck from util-linux 2.36.2
fsck.fat 4.1 (2017-01-24)
/dev/sdb: 0 files, 1/510992 clusters
Menggunakan gparted
sudo zypper in gparted
Pilih /dev/sdb
Klik kanan pilih format to
Pilih FAT32
Klik simbol centang
