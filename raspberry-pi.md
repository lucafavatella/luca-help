GPU bootloader and Linux kernel [ref](https://github.com/raspberrypi/firmware/blob/ffda51ebff205858df0f992ab2223a1c0c8c9525/README#L7-9) [other ref](https://thekandyancode.wordpress.com/2013/09/21/how-the-raspberry-pi-boots-up/)

The Raspberry Pi does [not](http://www.raspberrypi.org/forums/viewtopic.php?t=1444) support PXE but [can](http://elinux.org/RPi_U-Boot) boot U-Boot.

Debian armel [works](https://wiki.debian.org/RaspberryPi) on the Raspberry Pi, and [sid has](https://packages.debian.org/search?keywords=docker.io&searchon=names&suite=all&section=all) Docker.

Images:
* [Debian](https://wiki.debian.org/RaspberryPi)
* [FreedomBox](https://wiki.debian.org/FreedomBox/Hardware/RaspberryPi) [1](https://github.com/freedombox/freedom-maker/blob/4e91b4275bf28c4ad4c6d415df13d8558cf7542d/freedommaker/hardware-setup#L67-L92)
* [Raspbian](https://www.raspbian.org/)
* Raspberry Pi Foundation's [Raspbian](https://www.raspberrypi.org/downloads/raspbian/)
* [Nerves](https://github.com/nerves-project/nerves_system_rpi)
* Also [rpi-update](https://github.com/Hexxeh/rpi-update/blob/850f420871fe0a1fdd13f511ac0575e637530051/README.md#root_path-and-boot_path)
