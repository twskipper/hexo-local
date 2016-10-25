---
title: '命令总结（一): find'
tags:
  - linux
  - shell
id: 429
categories:
  - linux
  - shells
date: 2016-01-09 00:38:49
---

find算是平时使用比较频繁的命令
总结一下(参考书籍和man find)
find 命令
find命令的一般形式如下:
<pre>
find pathname -option [- print -exec -ok ...]
</pre>

pathname 就是查找的目录路径 . 就是当前路径
-print: 表示find 命令将匹配的文件输出的标准输出中
-exec: 表示find命令对匹配的文件执行该参数锁给出的shell命令。相应命令的形式为
‘command’ {} \ ; #因为{}在shell中又特殊意义，因此要用\来转义。
-ok: 作用和-exec相同，但是会在执行命令的时候给出询问。推荐在执行rm mv chmod的命令前添加-ok

<!--more-->

-option:（*表示常用）
-name * 按照文件名查找文件
-perm * e.g. find . -perm 755 -exec ls -l {} \; 找出当前目录下755权限的文件
-prune 直接使用可以不再当前目录查找。不过可以配合-path -prune -o过滤指定目录。
-user 按照文件所有者来查找
-group 按照所属组
-nogroup
-nouser

-mtime -n|+n 按照文件 更改 时间来查找 -n表示n天内，+n指n天前
-atime ... 按照文件的 访问 时间来查找
-ctime ... 按照文件 创建 时间 来查找

还有对应的分钟级别的
-mmin
-amin
-cmin

-type 查找某个类型的文件（目录也是文件linux一切皆文件）
b: 表示块设备文件 一般都是/dev/下的文件
d: * 表示目录
c: 表示字符设备文件 #比如/dev/null /dev/zero tty什么的。
p: 表示管道文件 #
l: * 表示符号链接文件
f: * 表示普通文件 最为常用 推荐使用，能加快查找速度

-size +/- n[cwbkMG] 查找文件大小为指定的大小 +表示大于 e.g. find . -size +19M
-depth: 查找文件时，首先查找当前目录的文件，在查询子目录。
-fstype: 在指定的文件系统中查找文件.查询/etc/fstab查看系统文件系统。

-mount: 表示在查找文件时不跨越文件系统mount点
-newer file1 !file2 查找更改时间比file1早 是比file2晚的文件

-follow 如果查找到的文件是链接文件就追踪到指向的文件。

参考:《构建高可用linux服务器》于洪春

优秀博客:

[http://www.cnblogs.com/wanqieddy/archive/2011/06/09/2076785.html](http://www.cnblogs.com/wanqieddy/archive/2011/06/09/2076785.html)

&nbsp;