---
title: mysql安全用户的做法，删除root账户
tags:
  - mysql
  - config
categories:
  - Docs
date: 2015-12-14 17:20:36
permalink: mysql-safe-tips-0
---

全部删除用户，添加额外管理员

<pre class="lang:mysql decode:true " >
delete from mysql.user;
grant all privileges on *.* to system@'localhost' identified by 'new-password' with grant option;
flush privileges;</pre>

	修改密码

<pre class="lang:mysql decode:true " >
update mysql.user set password=PASSWORD('yourpw') where user='user';
flush privileges;</pre>

	重新登录

<pre class="lang:mysql decode:true " >
mysql -u system -p</pre>
