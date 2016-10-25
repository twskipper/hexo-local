---
title: goaccess 分析nginx日志
tags:
  - 实用工具
id: 401
categories:
  - linux
  - shells
  - 实用工具
date: 2015-12-25 23:41:00
---

以我自己的阿里云主机为例
环境:
CentOS6.5
LAMP
运行的wordpress

yum源:阿里云的epel源
地址:
**http://mirrors.aliyun.com/help/epel

**

goaccess官网
[http://goaccess.io/](http://goaccess.io/)

<!--more-->

&nbsp;

安装goaccess
<pre class="lang:sh decode:true ">yum install -y goaccess</pre>
&nbsp;

配置crontab 每天晚上11点生成分析文件
**crontab -e**
输入以下内容
<pre class="lang:sh decode:true ">0  23  *  *  * /usr/bin/goaccess -d -f /var/log/nginx/access.log -a  &gt;/www/log/nginxlog$(date +%y%m%d).html 2&gt;/dev/null</pre>
&nbsp;
然后配置阿里云的解析，做个log主机

配置个nginx虚拟主机就行了