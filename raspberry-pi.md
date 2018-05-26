## Boot

The Raspberry Pi does [not](http://www.raspberrypi.org/forums/viewtopic.php?t=1444) support PXE but [can](http://elinux.org/RPi_U-Boot) boot U-Boot.

Troubleshooting:
* Boot [1](http://elinux.org/index.php?title=R-Pi_Troubleshooting&oldid=408541#Power_.2F_Start-up) [2](https://www.raspberrypi.org/forums/viewtopic.php?p=437084)

## Images

* [Raspberry Pi Foundation's recommended image of Raspbian](https://www.raspberrypi.org/downloads/raspbian/) (based on [original Raspbian](https://www.raspbian.org/))
  * Kernel [builds](https://github.com/raspberrypi/firmware/commits/master/boot) and [source](https://github.com/raspberrypi/linux/commits);
  * How to recompile Linux kernel module:

        ```
        ## Determine kernel versioned source.
        uname -a
        ## Sample output:
        ## > Linux raspberrypi 4.14.34+ #1110 Mon Apr 16 14:51:42 BST 2018 armv6l GNU/Linux
        dpkg-query -W raspberrypi-kernel firmware-misc-nonfree
        ## Sample output:
        ## > firmware-misc-nonfree   20170823-1
        ## > raspberrypi-kernel      1.20180417-1
        ## Kernel versioned source: tag `raspberrypi-kernel_1.20180417-1` at https://github.com/raspberrypi/linux.git
        ## Recompile on `pi@raspberrypi` module e.g. `mt7601u`.
        ## Clone kernel commit to compile - probably a patched version e.g. `git clone -b mt7601u-dma --depth 1 https://github.com/lucafavatella/linux.git linux`.
        git clone -b raspberrypi-kernel_1.20180417-1 https://github.com/raspberrypi/linux.git linux
        cd linux
        git rev-parse HEAD
        ## Perform sanity check that source refers to running kernel.
        head Makefile
        uname -r
        ## Copy kernel `.config` used to build the kernel.
        #sudo modprobe configs
        zcat /proc/config.gz > .config
        make drivers/net/wireless/mediatek/mt7601u/mt7601u.ko
        ```

  * WiFi dongles:
    * [Official BCM43143-based](https://www.raspberrypi.org/products/raspberry-pi-usb-wifi-dongle/);
    * [`mt7601u` (`ID 148f:7601 Ralink Technology, Corp.`?)](https://git.kernel.org/pub/scm/linux/kernel/git/stable/linux-stable.git/log/drivers/net/wireless/mediatek?h=linux-4.14.y).
      * [Working as of Sep 2015](https://github.com/raspberrypi/firmware/commit/13aa07f322b6f1645508b5c24ad70035f2a963d5);
      * [Potentially not working as of Apr 2016 "as soon as clock was enabled in I2S driver the USB bus (my wifi connection)" ... `Apr 24 20:34:33 Akkordion2B3 kernel: mt7601u 1-1.5:1.0: mt7601u_rxdc_cal timed out`](https://github.com/raspberrypi/linux/issues/1231#issuecomment-214044073);
      * Surely [relevant](https://github.com/openwrt/mt76/issues/139#issuecomment-388257649) patches [1](https://github.com/openwrt/mt76/commit/ad0a3e912a16c7cc1325a2bfc42a803a45efa26a) [2](https://github.com/openwrt/mt76/commit/a343cb68676b7172d4f3d0b0b1cb78cc8dc70ac1) for related device: 
      * Potentially relevant [mis](https://github.com/raspberrypi/linux/tree/raspberrypi-kernel_1.20180417-1/drivers/net/wireless/mediatek/mt7601u)[sing](https://git.kernel.org/pub/scm/linux/kernel/git/stable/linux-stable.git/log/drivers/net/wireless/mediatek/mt7601u?h=v4.14.34) [patch](https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/commit/drivers/net/wireless/mediatek/mt7601u?h=v4.17-rc5&id=fee05843801c37e527dbe2c5eeb3fb3b15bc9919).
  * WiFi:
    * Raspbian doc [1](https://www.raspberrypi.org/documentation/configuration/wireless/wireless-cli.md) [2](https://github.com/raspberrypi/documentation/pull/790);
    * [Debian doc 1](https://wiki.debian.org/WiFi/HowToUse?action=recall&rev=69#WPA-PSK_and_WPA2-PSK):

        ```
        pi@raspberrypi:~ $ cat /etc/network/interfaces.d/wlan0
        auto wlan0
        iface wlan0 inet dhcp
                wpa-ssid MyNetWork
                # plaintext passphrase
                wpa-psk plaintextsecret
        ```

  * Security ([1](https://www.raspberrypi.org/documentation/linux/usage/users.md) [2](https://www.raspberrypi.org/documentation/configuration/security.md)), tasks ([cron](https://www.raspberrypi.org/documentation/linux/usage/cron.md), [init](https://www.raspberrypi.org/documentation/linux/usage/rc-local.md)).
* [FreeBSD](https://wiki.freebsd.org/FreeBSD/arm/Raspberry%20Pi)
* [Nerves](https://github.com/nerves-project/nerves_system_rpi), based on Buildroot ([1](https://git.busybox.net/buildroot/tree/board/raspberrypi/readme.txt?id=03f6e005e6a9617767b24a9026da9477848020cc) [2](https://git.busybox.net/buildroot/tree/configs/raspberrypi_defconfig?id=03f6e005e6a9617767b24a9026da9477848020cc))

## Applications

### VPN

http://www.pivpn.io/
* Troubleshooting:
  * [UFW rules absent after reboot (uninstall `netfilter-persistent`/`iptables-persistent`)](https://github.com/pivpn/pivpn/issues/414).
