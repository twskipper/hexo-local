---
title: 'lua编译报错libreadline.so: undefined reference to'
tags:
  - linux
  - 排错
id: 173
categories:
  - linux
  - 排错
date: 2015-11-18 14:01:33
---

因为编译lua需要readline
readline又需要ncurses
修改lua安装包src/MakeFile 109行

<pre class="lang:default decode:true " >linux: $(MAKE) $(ALL) SYSCFLAGS="-DLUA_USE_LINUX" SYSLIBS="-Wl,-E -ldl -lreadline -lncurses"</pre> 