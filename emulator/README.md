# Raspberry Pi Emulator

This describes a way to run a Raspberry Pi emulator using QEMU. It is written for Arch Linux but 
the techniques can be applied to other distributions.

## Setup

The setup script will install QEMU if it is not already installed. It will download a filesystem image, 
a kernel image and set up a data disk.
Run as-is or modify it for your needs.

Once the setup script completes, you will have

1. QEMU installed
2. A system image
3. A kernel image
4. A data disk image

## Fix-up the system image

You need to modify /etc/fstab within the image to change the /boot partition's device
from /dev/mmcblk0 to /dev/sda1. Use rpi_mount:

    $ sudo ../disk/rpi_mount archlinux-hf-2012-09-18.img /mnt

Edit /mnt/etc/fstab. Change

    /dev/mmcblk0p1  /boot  vfat  defaults   0       0

to

    /dev/sda1       /boot  vfat  defaults   0       0

and then unmount:

    $ sudo ../disk/rpi_umount /mnt

## Booting

The boot script will start QEMU using the images prepared by the setup script.
Run as-is or modify it for your needs.

## Networking

The default network stack works. Note that using 'ping' to test the network connection will give the
impression that it isn''t working. This is because ICMP traffic does does not work and is a limitation
of the basic network stack, called SLIRP, provided by QEMU.

## Data Disk

The data disk image is presented as /dev/sdb. This needs to be formatted and mounted before use. 
Boot the emulator and then do:

    $ mkfs.ext4 /dev/sdb
    $ mount /dev/sdb /mnt

## Acknowledgements

Getting Raspberry Pi up and running in QEMU was quick and painless thanks to [this tutorial](http://xecdesign.com/qemu-emulating-raspberry-pi-the-easy-way). This worked first time for me with the default qemu package on Arch Linux and the archlinuxarm-13-06-2012.img.
Also, thanks to that site, updating to hardfloat was also straightforward. Tested against archlinux-hf-2012-09-18.img.




