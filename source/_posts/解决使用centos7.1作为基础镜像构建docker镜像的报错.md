---
title: 解决使用centos7.1作为基础镜像构建docker镜像的报错
categories:
  - Docs
date: 2016-08-23 17:28:58
tags:
  - linux
  - docker
  - config
  - errors
permalink: centos7-docker-error-0  
---

fakesystemd-1-17.el7.centos.noarch has installed conflicts systemd: fakesystemd-1-17.el7.centos.noarch

在Dockerfile里面增加
``` bash
RUN yum swap -y fakesystemd systemd \
&& yum install -y systemd-devel
```
