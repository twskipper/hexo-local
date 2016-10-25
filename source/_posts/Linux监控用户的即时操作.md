---
title: Linux监控用户的即时操作
tags:
  - linux
  - shell
id: 396
categories:
  - linux
date: 2015-12-25 16:38:00
---

利用 
PROMPT_COMMAND

在/etc/profile添加

PROMPT_COMMAND="history -a; $PROMPT_COMMAND"
<!--more-->

&nbsp;

这样用户完成命令后就回history-a 将记录保存到$HOME/.bash_history里面
写个脚本即时监控这些文件即可。
比如
先修改
默认history路径比较好
HISTORY_FILE=/var/log/usercmd/$(whoami).log
然后监控
tail -f /root/.bash_history &gt;/var/log/usercmd/root.log

如果有监控平台比如
可以在平台上监控这个日志，可以即时打印出来，也挺不错的。（那输入密码怎么办。。。。？？？）

&nbsp;

补充:
	此方法只能监控到已经完成的命令，不过想想，要监控用户正在输入的内容还挺难的，不知道有没有实现方法。