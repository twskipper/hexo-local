---
title: openwrt
permalink: openwrt-pkg-tip1
tags:
  - openwrt
  - config
id: 90
categories:
  - Docs
date: 2015-10-24 19:35:15
---

Openwrt安装USB驱动挂载U盘

<pre class="toolbar:1 lang:default decode:true " >opkg update
opkg install kmod-usb-core
opkg install kmod-usb-ohci #安装usb ohci控制器驱动
#opkg install kmod-usb-uhci 　#UHCI　USB控制器
opkg install kmod-usb2 #安装usb2.0
opkg install kmod-usb-storage #安装usb存储设备驱动
opkg install usbutils #安装了这个后可以用 lsusb
opkg install kmod-fs-ext2 #安装ext2分区支持
opkg install kmod-fs-ext3 #安装ext3分区格式支持组件
opkg install kmod-fs-ntfs #ntfs内核驱动
opkg install kmod-nls-cp437    #非常关键
opkg install kmod-nls-iso8859-1 #非常关键
opkg install mount.ntfs-3g #挂载ntfs助手
opkg install mount-utils #挂载卸载工具
opkg install ntfs-3g #挂载NTFS
opkg install kmod-fs-vfat #挂载FAT
opkg install fdisk #硬盘分区管理工具
</pre> 

挂载分区：
``` bash
mount  /dev/sda1 /mnt/
```
开机自动挂载：