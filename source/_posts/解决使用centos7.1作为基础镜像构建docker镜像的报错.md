---
title: 解决使用centos7.1作为基础镜像构建docker镜像的报错
id: 580
comment: false
categories:
  - docker
  - linux
  - 排错
date: 2016-08-23 17:28:58
tags:
---

fakesystemd-1-17.el7.centos.noarch has installed conflicts systemd: fakesystemd-1-17.el7.centos.noarch

在Dockerfile里面增加

    RUN yum swap -y fakesystemd systemd &amp;&amp; \
        yum install -y systemd-devel