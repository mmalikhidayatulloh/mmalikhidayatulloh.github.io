# Run Installer

```
void-installer
```

# Login

username : `root`

password : `voidlinux`

# Choose Keyboard

Usually everyone use `US` keyboard

# Network

Select your internet connetion. Use ethernet or wifi. Then click ok when there is question to use DHCP.

# Source

There are two options here. use local source or network source. if you have good internet connection you can choose `Network` and download the source from their official repository. but if your internet connection are bad, you have to choose Local source. I recomended use Local source to save my internet quota.

# Hostname

type hostname to give your computer name as like as you want.

# Locale

in this section usually choose `en_US.UTF-8`

# Timezone

Select your time zone, in this section i choose `Asia/Jakarta`

# Root Password

input your root password

# User Account

make ordinary user therewith password. Example:

username : `Mamal`
password : `123456789`

Then just hit ok when select the group to select default settings.

# BootLoader

Just hit enter at your hard disk, and answer yes at select graphical bootloader

# Partitions

Just hit enter at your hard disk, then choose label type for your partitions, if your computer is UEFI your have to choose `gpt` but if your computer is MBR or Legacy you have to choose `dos`.

To create partitions just hit `New` at free space

Then input partition size in M for Megabyte or G for Gigabyte.

Then select type of your partition. Example: UEFI system, Linux Swap, or Linux File System.

After finish all, select `Write` and answer `yes` then hit enter and `Quit`. 

# File System

Choose your partitions. If you use UEFI you have to choose `vfat` and set mount point at `/boot/efi`, and for root partition usually choose `ext4` and set mount at `/`

# Install

Answer yes to install the system

After finish installation, reboot the system.