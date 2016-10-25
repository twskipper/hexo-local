---
title: 'CenOS7 lvm扩容报错resize2fs: Bad magic number in super-block'
tags:
  - errors
  - linux
  - lvm
categories:
  - Docs
date: 2015-10-21 14:49:13
permalink: centos7-lvm-erros-resize2fs
---
问题，用centos7对lvm进行扩容操作时，执行
resize2fs 命令时报错
resize2fs: Bad magic number in super-block
而且df查看文件系统没有扩容
但是lvdisplay能查看已经扩容成功

解决：
centos7默认使用xfs文件系统
把resize2fs 换成 xfs_growfs
即可
