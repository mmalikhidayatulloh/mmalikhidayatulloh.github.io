Creating bootable USB flash drive from a Terminal on Linux 

Plug in the USB flash drive.

Find out the name of your USB drive with `ls -l /dev/disk/by-id/usb-*` and check with lsblk to make sure that it is not mounted
```
sudo umount /dev/sdX*
```
To restore the USB drive as an empty, usable storage device after using ISO image, the `ISO 9660` filesystem signature needs to be removed by running
```
# wipefs --all /dev/disk/by-id/usb-My_flash_drive
```
as root

Then
# using cat:
```
# cat path/to/archlinux-version-x86_64.iso > /dev/disk/by-id/usb-My_flash_drive
```
# using cp:
```
# cp path/to/archlinux-version-x86_64.iso /dev/disk/by-id/usb-My_flash_drive
```
# using dd:
```
# dd bs=4M if=path/to/image.iso of=/dev/disk/by-id/usb-My_flash_drive conv=fsync oflag=direct status=progress
```
# using tee:
```
# tee < path/to/archlinux-version-x86_64.iso > /dev/disk/by-id/usb-My_flash_drive
```
# using pv:
```
# pv path/to/archlinux-version-x86_64.iso -Yo /dev/disk/by-id/usb-My_flash_drive
```
