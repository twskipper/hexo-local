---
title: goaccess 分析nginx日志
tags:
  - linux
  - nginx
categories:
  - Docs
date: 2015-12-25 23:41:00
permalink: goacess-nginx-0
---

以我自己的阿里云主机为例
环境:
CentOS6.5
LAMP
运行的wordpress

yum源:阿里云的epel源
地址:
[aliyun_mirros](http://mirrors.aliyun.com/help/epel)

goaccess官网
[http://goaccess.io/](http://goaccess.io/)

安装goaccess
yum install -y goaccess
配置crontab 每天晚上11点生成分析文件

crontab -e
输入以下内容
0  23  *  *  * /usr/bin/goaccess -d -f /var/log/nginx/access.log -a  > /www/log/nginxlog$(date +%y%m%d).html >/dev/null 2>&1

### 然后就可以打开看了。不过是英文版的。
