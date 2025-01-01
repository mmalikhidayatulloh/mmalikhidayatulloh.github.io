Creating bootable USB flash drive from a Terminal on Linux 
Plug in the USB flash drive.

Find the corresponding device with lsblk. You can distinguish them by their size.

Make sure all partitions on the device are properly unmounted. Replace sdX with your device (e.g. sdb).

sudo umount /dev/sdX*
Then use the dd utility to write the image to the USB flash drive.

sudo dd bs=4M conv=fsync oflag=direct status=progress if=<path-to-image> of=/dev/sdX
