## Boot

The Raspberry Pi does [not](http://www.raspberrypi.org/forums/viewtopic.php?t=1444) support PXE but [can](http://elinux.org/RPi_U-Boot) boot U-Boot.

Troubleshooting:
* Boot [1](http://elinux.org/index.php?title=R-Pi_Troubleshooting&oldid=408541#Power_.2F_Start-up) [2](https://www.raspberrypi.org/forums/viewtopic.php?p=437084)

## Images

* [Raspberry Pi Foundation's recommended image of Raspbian](https://www.raspberrypi.org/downloads/raspbian/) (based on [original Raspbian](https://www.raspbian.org/))
  * Kernel [builds](https://github.com/raspberrypi/firmware/commits/master/boot) and [source](https://github.com/raspberrypi/linux/commits);
  * WiFi dongles:
    * [Official BCM43143-based](https://www.raspberrypi.org/products/raspberry-pi-usb-wifi-dongle/);
    * [`mt7601u` (`ID 148f:7601 Ralink Technology, Corp.`?)](https://git.kernel.org/pub/scm/linux/kernel/git/stable/linux-stable.git/log/drivers/net/wireless/mediatek?h=linux-4.14.y
).
      * [Working as of Sep 2015](https://github.com/raspberrypi/firmware/commit/13aa07f322b6f1645508b5c24ad70035f2a963d5);
      * [Potentially not working as of Apr 2016 "as soon as clock was enabled in I2S driver the USB bus (my wifi connection)" ... `Apr 24 20:34:33 Akkordion2B3 kernel: mt7601u 1-1.5:1.0: mt7601u_rxdc_cal timed out`](https://github.com/raspberrypi/linux/issues/1231#issuecomment-214044073).
  * Security ([1](https://www.raspberrypi.org/documentation/linux/usage/users.md) [2](https://www.raspberrypi.org/documentation/configuration/security.md)), tasks ([cron](https://www.raspberrypi.org/documentation/linux/usage/cron.md), [init](https://www.raspberrypi.org/documentation/linux/usage/rc-local.md)).
* [FreeBSD](https://wiki.freebsd.org/FreeBSD/arm/Raspberry%20Pi)
* [Nerves](https://github.com/nerves-project/nerves_system_rpi), based on Buildroot ([1](https://git.busybox.net/buildroot/tree/board/raspberrypi/readme.txt?id=03f6e005e6a9617767b24a9026da9477848020cc) [2](https://git.busybox.net/buildroot/tree/configs/raspberrypi_defconfig?id=03f6e005e6a9617767b24a9026da9477848020cc))

## Applications

### VPN

http://www.pivpn.io/
* Troubleshooting:
  * [UFW rules absent after reboot (uninstall `netfilter-persistent`/`iptables-persistent`)](https://github.com/pivpn/pivpn/issues/414).
