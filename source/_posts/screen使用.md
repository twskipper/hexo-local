---
title: screen  一个实用的工具
permalink: screen-usage
tags:
  - linux
  - shell
  - 实用工具
id: 195
categories:
  - Docs
date: 2015-12-01 14:33:01
---

这几天因为水晶头的原因导致我登陆远程ssh的时候老是掉线，然后就是悲剧。就想找一个有没有能在我掉线的时候，帮我保存ssh状态的软件。果然让我找到了，就是这个screen。
centos/rhel 直接使用 

<pre class="lang:sh decode:true " >yum install screen</pre> 

 即可使用

常用方法
用name创建一个screen

<pre class="lang:sh decode:true " >screen -S name </pre> 

退出可以使用exit
<!--more-->

如果想暂时离开一会还要用就用
ctrl -a d
就是按住ctrl 然后依次按下a和d

screen -ls 查看已经有的screen

<pre class="lang:sh decode:true " >[root@xhmysql ~]# screen -ls
There are screens on:
 21065.mysql (Detached)
 3909.x (Detached)
 Sockets in /var/run/screen/S-root.</pre> 

恢复screen
screen -r pid 恢复screen

<pre class="lang:sh decode:true " >[root@xhmysql ~]# screen -D -r 21065
</pre> 

tips:

可以使用screen -D -r pid 恢复还被占用的screen.
&nbsp;

&nbsp;

一个IBM的文档写的非常好
[http://www.ibm.com/developerworks/cn/linux/l-cn-screen/](http://www.ibm.com/developerworks/cn/linux/l-cn-screen/)
这个也不错
[http://www.cnblogs.com/ywl925/p/3604530.html](http://www.cnblogs.com/ywl925/p/3604530.html)