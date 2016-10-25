---
title: saltstack执行salt命令时很慢
permalink: salt-slow
tags:
  - saltstack
  - 优化
categories:
  - Docs
date: 2016-01-27 21:37:19
---

今天有个小伙伴问我为啥他的salt在执行命令的时候感觉响应的很慢。就是敲个命令半天才反应过来。

&nbsp;

原因: 没有做主机名解析。master端一定要能解析自己的主机名，可以使用dns，可以用hosts文件。

解决办法:

在hosts文件中添加本机的主机名解析。