---
title: keepalived 安装
tags:
  - linux
  - 配置
id: 391
categories:
  - linux
date: 2015-12-24 03:38:00
---

[![](http://www.inpeace.cn/wp-content/uploads/2015/12/1450957123.gif)](http://www.inpeace.cn/wp-content/uploads/2015/12/1450957123.gif)

keepalived
软件类型：高可用集群软件

	VRRP协议介绍
		虚拟路由器冗余协议
		通过竞选协议机制，解决静态路由的单点故障
		使用IP多播方式实现通信
		master发送数据包，备份收数据包，当备一定时间内收不到的时候，接管master
<!--more-->

功能
		healthcheck

failover

安装配置
	依赖openssl

**yum install openssl openssl-devel -y**

下载
	 **wget http://www.keepalived.org/software/keepalived-1.1.19.tar.gz
**
	** tar xf ke~
	 cd keepaliv~**

** ./configure**
	 	编译参数 --sysconf=/etc

**make &amp;&amp; make install **

配置

拷贝启动脚本
	 **cp /usr/local/etc/rc.d/init.d/keepalived /etc/init.d/**

拷贝系统配置文件
	 **cp /usr/local/etc/sysconfig/keepalived /etc/sysconfig/**

创建keepalived配置文件目录
	** mkdir -p /etc/keepalived**

**cp /usr/local/etc/keepalived/keepalived.conf /etc/keepalived/**

** cp /usr/local/sbin/keepalived /usr/sbin/**

	 启动
	** /etc/init.d/keepalived start
	 ps -ef|grep keep**

关闭
	 **/etc/init.d/keepalived stop

**