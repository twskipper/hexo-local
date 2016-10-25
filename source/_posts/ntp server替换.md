---
title: api.ntp.bz最近好像不能用了?更换新的ntp服务器地址
permalink: new-ntp-server-domain
tags:
  - linux
  - config
id: 632
comment: false
categories:
  - Docs
date: 2016-09-30 09:50:19
---

最近线上几台机器出现莫名的时间有也偏差，查询了一下采用的ntp服务器有些问题

[ntp.api.bz](http://api.bz)好像不能用了。

多好的东西啊。现在已经更换成
``` bash
ntpdate 0.pool.ntp.org
```
这个了。