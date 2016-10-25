---
title: logstash 2.3 启动脚本 简陋版
tags:
  - shell
id: 546
categories:
  - linux
  - shells
date: 2016-05-10 17:54:19
---

本脚本是用于启动logstash的脚本在ubuntu 14.04.3测试通过

根据自己的需要
请修改一下内容:

<pre class="lang:sh decode:true " >logstash_bin=""
logstash_conf=""
logstash_log=""
pid_file=""</pre> 

**的值为你的logstash bin目录路径 配置文件绝对路径 log绝对路径**

<pre class="lang:sh decode:true" title="logstash.init">#!/bin/bash
#www.inpeace.cn
#skipper i@inpeace.cn for logstash 2.3.1
#please check your java env right
#v0.1 20160510
logstash_bin=""
logstash_conf=""
logstash_log=""
pid_file=""
pid=$(ps -ef|grep java|grep logstash|awk '{print $2}')

start () {
	echo "Now starting logstash it will cost a little time"
        ${logstash_bin}/logstash -f ${logstash_conf} -r -l ${logstash_log} &amp; &gt;/dev/null 2&gt;&amp;1
	echo $pid &gt; ${pid_file} 
}

stop () {
	echo "Stoping logstash"
	kill $pid
}

restart () {
	stop
	start
}

case $1 in
        start)
                start
                ;;
        stop)
                stop
                ;;
        restart)
                stop
                start
                ;;
        *)
                echo "Usage: $0 {start|stop|restart|}"
                exit 1
                ;;
esac

exit 0
</pre>