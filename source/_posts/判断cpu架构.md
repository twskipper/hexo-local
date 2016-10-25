---
title: 判断linux系统是32位还是64位的一个命令
tags:
  - linux
  - shell
categories:
  - Docs
date: 2015-12-09 20:14:16
permalink: 32-or-64
---

 ``` bash
getconf LONG_BIT 
```
使用
``` bash
uname -m 
```
也是可以的但是偶然发现的这个命令,感觉高大上.