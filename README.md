# NanoPI Neo Yocto setup

Yocto setup:


the following actions are needed:
1. git clone git://git.yoctoproject.org/poky
2. cd poky
3. git clone git://github.com/linux-sunxi/meta-sunxi
4. source oe-init-build-env
5. MACHINE=nanopi-neo bitbake core-image-minimal

this should take a while (3 hrs) to finish the build. The image will be located here:

```
poky/build/tmp/deploy/images/nanopi-neo
```




Flashing on to SDCard:


Insert SDcard and check the medium in sudo dmesg command.

if there are partitions already, then delete them with fdisk /dev/sdb.

Insert back and perform dd command.

```
dd if=core-image-minimal-nanopi-neo-20220217185745.rootfs.sunxi-sdimg of=/dev/sdb
```




Serial console setup:


Neo board have two interfaces for UART but only one works well. It will be located beside the USB connector. Flip the board and observe the pin names.

Set the serial cable pins this way on the neo board.
1. black - ground
2. green - rx
3. white - tx




Booting:




Boot is simpler, just insert SD card, apply power through USB OTG cable. USB connection to the host laptop also powers the nanopi neo.

Once serial is setup and power is applied, validate the boot.


