The specification commonly used for [network booting](https://en.wikipedia.org/wiki/Network_booting) is [PXE](https://en.wikipedia.org/wiki/Preboot_Execution_Environment), based on DHCP and TFTP.

The PXE client is usually found in the BIOS/NIC/UEFI.

An open-source PXE client is iPXE, another is U-Boot.
coreboot [can](http://www.coreboot.org/Payloads) boot a PXE client.

NixOS [supports](https://nixos.org/manual/nixos/stable/index.html#sec-booting-from-pxe) being booted from a PXE client.

A curated set of PXE-bootable operating systems is at https://github.com/netbootxyz/netboot.xyz
that [supports self-hosting](https://netboot.xyz/docs/selfhosting/).
It also documents [how to setup DHCP server and TFTP server](https://netboot.xyz/docs/booting/tftp/).

NixOS is listed on https://netboot.xyz/docs/changelog/#2041---2021-07-08
as mentioned on [its wiki](https://nixos.wiki/wiki/Netboot).

An example of PXE boot with NixOS is https://blog.6aa4fd.com/post/ipxe-nix-ci/
