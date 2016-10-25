---
title: python自动补全（tab）
permalink: python-auto-tab
tags:
  - python
categories:
  - Docs
date: 2015-10-20 14:25:03
---

方法一：（python自动补全tab脚本 只在centos 和osx 测试过)
1,执行以下命令

<pre class="toolbar:1 lang:default decode:true " >wget http://file.inpeace.cn/autotab.sh</pre> 
2,然后执行

<pre class="lang:default decode:true " >source autotab.sh </pre> 

方法二：
<!--more-->

1，在~目录下创建 .pythonstartup文件。

<pre class="lang:default decode:true " >[root@7 ~]# vi .pythonstartup
</pre> 

2,复制以下内容至.pythonstartup文件内

<pre class="theme:eclipse toolbar:1 toolbar-overlay:false lang:python decode:true " >
#!/usr/bin/python 
# python startup file 

import sys
import readline
import rlcompleter
import atexit
import os

readline.parse_and_bind('tab: complete')

historyfile = os.path.join(os.environ['HOME'],'.pythonhistory')
try:
        readline.read_history_file(historyfile)
except IOError:
        pass
atexit.register(readline.write_history_file,historyfile)
del os,historyfile,readline,rlcompleter
###from inpeace.cn</pre> 

3，打开bash环境变量配置文件

<pre class="lang:default decode:true " >[root@7 ~]# vi ~/.bashrc 
</pre> 
添加如下内容至文件末尾

<pre class="lang:default decode:true " >export PYTHONSTARTUP=~/.pythonstartup
</pre> 
或者直接直接执行

<pre class="lang:default decode:true " >echo "export PYTHONSTARTUP=~/.pythonstartup" &gt;&gt; ~/.bashrc
</pre> 

4 使环境变量生效

<pre class="lang:default decode:true " >source ~/.bashrc</pre> 

查看结果