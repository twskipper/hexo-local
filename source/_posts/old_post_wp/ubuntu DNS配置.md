---
title: ubuntu 永久DNS设置
permalink: resolv-config
tags:
  - linux
  - config
categories:
  - Docs
date: 2016-08-31 14:30:12
---

如果简单修改 /etc/resolv.conf, 在机器重启后，会失效，您的修改会被默认配置覆盖掉。

比较持久的做法是，
``` bash
sudo vim /etc/resolvconf/resolv.conf.d/tail
```
增加2条
``` plain
nameserver 114.114.114.114
nameserver 119.29.29.29
```
然后重启一下名称服务 

``` bash
sudo /etc/init.d/resolvconf restart
```
