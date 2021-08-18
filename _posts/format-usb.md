 
{:toc}

# Menggunakan Terminal

Cek dulu directory usb-nya

```
df
```

Nama usb biasanya

```
/dev/sdb
```

## Umount

```
sudo umount /dev/sdb
```

## Format

Untuk memformat USB drive menjadi format `FAT32`:

```
sudo mkfs.vfat /dev/sdb
```

Untuk memformat USB drive menjadi format `NTFS`:

```
sudo mkfs.ntfs /dev/sdb
```

Untuk memformat USB drive ke dalam format `exFAT`:

```
sudo mkfs.exfat /dev/sdb
```

## Konfirmasi bahwa pemformatan berhasil:

```
sudo fsck /dev/sdb
```

Hasil:

```
~ >>> sudo fsck /dev/sdb                                                                        
fsck from util-linux 2.36.2
fsck.fat 4.1 (2017-01-24)
/dev/sdb: 0 files, 1/510992 clusters
```

# Menggunakan gparted

## Install Gparted

```
sudo zypper in gparted
```

## Cara memformat

Pilih `/dev/sdb`

Klik kanan pilih `format to`

Pilih `FAT32` (atau format lain)

Klik tanda centang