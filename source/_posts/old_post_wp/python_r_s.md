---
title: "python中\r和，"
permalink: python-print-tips-1
tags:
  - python
id: 126
categories:
  - Docs
date: 2015-10-30 22:38:53
---

\r表示 光标移动到开头 ，表示不换行
比如 
<pre class="lang:default decode:true " >print 'finally done\r',
print 'aaaa\ri'
print 'bbbbbbbbbbbbbbbbbb',
print 'ccc'</pre> 

执行结果是

<pre class="lang:default decode:true " >[root@inpeace inpeace.cn]# python demo.py 
iaaally done
bbbbbbbbbbbbbbbbbb ccc
</pre> 
<!--more-->

比如这个
<pre class="lang:default decode:true " >while True:
    for i in ["/","-","|","\\","|"]:
        print "%s\r" % i,</pre> 
官方解释
We put a , (comma) at the end of each print line. This is so print doesn't end the line with a newline character and go to the next line.