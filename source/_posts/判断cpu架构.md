---
title: 判断linux系统是32位还是64位的一个命令
tags:
  - linux
  - 随笔
id: 271
categories:
  - linux
date: 2015-12-09 20:14:16
---

 ``` bash
getconf LONG_BIT 
```
使用uname -m 也是可以的但是偶然发现的这个命令,感觉高大上