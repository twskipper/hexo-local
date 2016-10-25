---
title: saltstack master端 刷新grains
permalink: salt-flush-grains
tags:
  - saltstack
  - linux
categories:
  - Docs
date: 2015-11-26 18:40:20
---

[http://docs.saltstack.cn/zh_CN/latest/topics/targeting/grains.html](http://docs.saltstack.cn/zh_CN/latest/topics/targeting/grains.html)
4.2.8\. 同步Grains

Syncing grains can be done a number of ways, they are automatically synced when state.highstate is called, or (as noted above) the grains can be manually synced and reloaded by calling the  

<pre class="lang:default decode:true " >saltutil.sync_grains or saltutil.sync_all functions.</pre> 

具体
``` bash
 salt '*' saltutil.sync_grains
```