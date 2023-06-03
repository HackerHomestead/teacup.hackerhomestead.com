# Slackware 15.1 on the Teacup

## Introduction
One of our community members uncovered a version of Slackware that works on the T31

Its very easy to get up and running on the Teacup RevA board. However it is not maintained any longer

{{< hint warning >}}
This is written as fast as possable, your YMMV
{{< /hint >}}

## Download Image
Primary Download: https://linode-tx-02.shortcutsolutions.net/slack.tar.gz 

Alt Download: https://www.hackerhomestead.com/files/teacup/slackware-mips/slack.tar.gz

{{< hint >}}
**MD5 Sum** ``7012210f843bf289cb48d9428c7cb4bd  slack.tar.gz``
{{< /hint >}}

## Install
Create 2 partitions on your SD card and format them. 
Small VFAT (I made mine 256M but only using 6M of that) for p1, ext3 (rest of the capacity) for p2. 
Mount p2 somewhere, create a boot directory inside and mount p1 to it. 
untar the slack archive into where you mounted p2 unmount both filesystems and the SD is ready to go


## u-boot stuff: 
```
env set bootcmd 'fatload mmc 0 0x1000000 uImage; bootm 0x1000000' 
env set bootargs 'mem=128M console=ttyS1,115200n8 panic=5 rootwait root=/dev/mmcblk0p2'
```

## To install new packages 
1. find the package at 
	- https://bonslack.org/15.1-curr/bonslack_mipsel-current/slackware/
	- https://www.hackerhomestead.com/files/teacup/slackware-mips/bonslack.org/15.1-curr/
1. download to the teacup, use 'installpkg [filename]' to install.
