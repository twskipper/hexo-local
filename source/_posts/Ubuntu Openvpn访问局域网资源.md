---
title: Ubuntu Openvpn访问局域网资源
permalink: ubuntu-openvpn-route
tags:
  - linux
  - config
categories:
  - Docs
date: 2016-09-07 15:47:00
---

在一台非网关设备架设openvpn
在配置好服务器后客户端无法访问局域网资源
*openvpn 客户端IP地址段是按照默认的配置即10.8.0.0/8网段

*以下所有配置都在服务器端*
*默认已经安装好服务端配置好证书*
如果没有请参考如下链接自行翻译
传送门:[openvpen on ubuntu 14.04](https://www.digitalocean.com/community/tutorials/how-to-set-up-an-openvpn-server-on-ubuntu-14-04 "openvpn")

服务器接口信息如下
```
eth0 192.168.1.0/24 内网资源
eth1 公网ip地址
```

配置openvpn server配置文件
``` bash
vim /etc/openvpn/server.conf
```

添加两条
```
push "route 192.168.1.0 255.255.255.0"
push "route 外网网段 255.255.255.128"
```



让客户端添加两条路由信息
启动ip转发
``` bash
echo 1 > /proc/sys/net/ipv4/ip_forward
```

##### 若要永久生效请手动修改sysctl.conf文件

修改防火墙以ubuntu ufw为例
让客户端可以访问这两个网卡
``` plain
vim /etc/ufw/before.rules
增加
# START OPENVPN RULES
# # NAT table rules
*nat
:POSTROUTING ACCEPT [0:0]
# Allow traffic from OpenVPN client to eth0
-A POSTROUTING -s 10.8.0.0/8 -o eth1 -j MASQUERADE
-A POSTROUTING -s 10.8.0.0/8 -o eth0 -j MASQUERADE
COMMIT
```

*不要删除这个文件上面的\*filter这条信息*

重启ufw
``` bash
ufw reload
```