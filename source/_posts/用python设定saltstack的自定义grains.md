---
title: 用python设定saltstack的自定义grains
tags:
  - python
  - saltstack
categories:
  - Docs
date: 2015-12-02 09:53:35
---

参考官方文档
[http://docs.saltstack.cn/zh_CN/latest/topics/targeting/grains.html#targeting-grains](http://docs.saltstack.cn/zh_CN/latest/topics/targeting/grains.html#targeting-grains)
The grains interface is derived by executing all of the "public" functions found in the modules located in the grains package or the custom grains directory. The functions in the modules of the grains must return a Python dict, where the keys in the dict are the names of the grains and the values are the values.

Custom grains should be placed in a _grains directory located under the file_roots specified by the master config file. The default path would be /srv/salt/_grains. Custom grains will be distributed to the minions when **state.highstat**e is run, or by executing the **saltutil.sync_grains** or **saltutil.sync_all** functions.
<!--more-->

Grains are easy to write, and only need to return a dictionary. A common approach would be code something similar to the following:

<pre class="lang:default decode:true " >#!/usr/bin/env python
def yourfunction():
     # initialize a grains dictionary
     grains = {}
     # Some code for logic that sets grains like
     grains['yourcustomgrain']=True
     grains['anothergrain']='somevalue'
     return grains
</pre> 

举个例子：配置web服务用到的max_open_file

<pre class="lang:default decode:true " >#!/usr/bin/env python

import os,sys,commands

def Grains_openfile():
        '''
        use ulimit -n get max_open_file then return to grians
        by skipper
        inpeace.cn
        '''
        grains = {}
        _open_file=65536
        try:
                getulimit=commands.getstatusoutput('source /etc/profile;ulimit -n')
        except Exception,e:
                pass
        if getulimit[0]==0:
                _open_file=int(getulimit[1])
        grains['max_open_file'] = _open_file
        return grains</pre> 

然后执行 

<pre class="lang:default decode:true " >salt '*' saltutil.sync_all</pre> 

使用 

<pre class="lang:default decode:true " >salt '*' grains.item max_open_file</pre> 

查看结果