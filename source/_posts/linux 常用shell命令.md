---
title: linux常用指令记录
tags:
  - linux
id: 643
comment: false
categories:
  - linux
date: 2016-10-21 10:55:59
---

此片文章将会记录日常工作学习到有用shell。方便日后查询

&nbsp;

查看进程按照内存大小排序
<pre class="lang:sh decode:true ">ps -e -o "%C : %p : %z : %a"|sort -k5 -nr</pre>
按照CPU排序
<pre class="lang:default decode:true ">ps -e -o "%C : %p : %z : %a"|sort -nr</pre>
剩余内存
<pre class="lang:default decode:true ">free -m |grep "Mem" | awk "{print $2}"</pre>
连接数
<pre class="lang:default decode:true ">netstat -an|awk '/^tcp/ {++S[$NF]} END {for (a in S) print a,S[a]}'</pre>
当前目录所有文件按照大小排序
<pre class="lang:default decode:true ">ll |awk '{print $9}'|grep -Ev '^\.'|xargs du -h|sort -h</pre>
curl使用用户名密码访问
<pre class="lang:default decode:true ">curl -u username:password url</pre>

过滤掉attac*,ucser* 还有当前目录根.
<pre class="lang:sh decode:true">ll |grep -e '^d'|awk '{print $9}'|grep -vE '(attac*|uc_ser*|\.)'|xargs du -sh</pre>
&nbsp;