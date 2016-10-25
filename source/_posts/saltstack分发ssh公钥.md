---
title: saltstack分发ssh公钥
permalink: salt-pub-ssh
tags:
  - saltstack
  - linux
categories:
  - Docs
date: 2016-01-06 07:47:57
---

&nbsp;

1，首先在master端创建公钥
``` bash
ssh-keygen -t rsa
```
2，创建/srv/salt/ssh文件夹
``` bash
mkdir -pv /srv/salt/ssh
```
3，将公钥拷贝到/srv/salt/ssh文件夹中
``` bash
cp /root/.ssh/id_rsa.pub /srv/salt/ssh/
```
<!--more-->

4，分发到minion端上
``` bash
salt ‘*’ ssh.set_auth_key_from_file root salt://ssh/id_rsa.pub
```
这样就可以直接使用ssh不用密码登陆了，不过第一次使用ssh连接需要添加ssh_known.