# Raspberry-Pi Utilities : Disk

Disk utilitles for working with SD cards and images.

Root privileges are required.

## rpi_mkimage

Use rpi_mkimage to prepare a fileystem image or device. see rpi_mkimage --help 
for further information.

## rpi_mount

Use rpi_mount to mount an image or device. It first mounts the root partition and
then mounts the boot partition on top. If mounting an image, it first creates
a loop device. Usage (as root):

    # rpi_mount img_or_device /mount/point

## rpi_unmount

Use rpi_umount to unmount an image or device mounted by the mount command described
above. It also removes any loop device used to mount an image. Usage (as root):

    # rpi_umount /mount/point

