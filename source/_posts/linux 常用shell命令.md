---
title: linux常用指令记录
tags:
  - linux
  - shell
categories:
  - Docs
date: 2016-10-21 10:55:59
permalink: linux-shell-command-notebook-0
---
*此片文章将会记录日常工作学习到有用shell。方便日后查询*
好记星不如烂笔头

``` bash
#查看进程按照内存大小排序
ps -e -o "%C : %p : %z : %a"|sort -k5 -nr
#按照CPU排序
ps -e -o "%C : %p : %z : %a"|sort -nr
#剩余内存
free -m |grep "Mem" | awk "{print $2}"
#统计TCP连接数
netstat -an|awk '/^tcp/ {++S[$NF]} END {for (a in S) print a,S[a]}'
##4w连接数以上用ss 需要安装iproute2
ss -t -a |grep -Ev 'State'|awk '{print $1}'|awk '{++C[$1]} END {for (i in C) print i,C[i]}'
#当前目录所有文件按照大小排序
ll |awk '{print $9}'|grep -Ev '^\.'|xargs du -h|sort -h
#curl使用用户名密码访问
curl -u username:password url
#过滤掉attac*,ucser* 还有当前目录根.
ll |grep -e '^d'|awk '{print $9}'|grep -vE '(attac*|uc_ser*|\.)'|xargs du -sh
# curl 返回http状态码 这个以后会更新新的博客介绍内置变量
curl -I -m 5 -o /dev/null -s -w %{http_code} https://mufen.me
```
