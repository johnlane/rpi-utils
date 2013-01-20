Kernel Build Notes
==================

QEMU ARM Emulator
-----------------

Use the script 'build-kernel-qemu' to build a kernel image that
can be used to boot QEMU. The script can build a soft or hard
float kernel. (for soft-float, comment out "HARDFLOAT=yes" near
the top of the script).

Assumptions
-----------

An appropriate cross compiler toolchain is available at:

* for soft float : /usr/bin/arm-linux-gnueabi-*
* for hard float : /usr/bin/arm-linux-gnueabihf-*

Tests
-----

Tested by booting Raspberry-Pi Arch Linux system images in QEMU:

* for soft float : archlinuxarm-13-06-2012.img
* for hard float : archlinux-hf-2012-09-18.img

References
----------
http://xecdesign.com/compiling-a-kernel/
http://balau82.wordpress.com/2010/03/22/compiling-linux-kernel-for-qemu-arm-emulator/
