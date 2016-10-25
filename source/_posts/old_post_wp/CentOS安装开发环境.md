---
title: CentOS安装开发环境
tags:
  - linux
  - config
categories:
  - Docs
date: 2015-12-16 09:30:46
permalink: cetnos-dev-pkgs
---

包括gcc 开发库，为以后编译各种软件做准备

``` bash
yum groupinstall -y "Compatibility libraries" "Base" "Development tools"
yum groupinstall -y "debugging Tools" "Dial-up Networking Support"
```
