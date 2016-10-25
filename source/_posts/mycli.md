---
title: mycli 自动补全 语法高亮
tags:
  - linux
  - mysql
  - 实用工具
id: 145
categories:
  - mysql
  - OSX
date: 2015-11-02 23:11:08
---

#### nice tool for mysql
安装指导
[http://mycli.net/install](http://mycli.net/install)
<pre class="lang:sh decode:true ">pip install mycli</pre>
&nbsp;

如果没有安装pip的话，先安装pip
<pre class="lang:sh decode:true ">yum install -y python-pip</pre>
或者使用
<pre class="lang:sh decode:true ">easy_install mycli</pre>
&nbsp;

2种用法
1,
<pre class="lang:default decode:true ">mycli mysql://root@localhost:3306</pre>

<pre class="lang:default decode:true ">mycli -h localhost -u root</pre>
