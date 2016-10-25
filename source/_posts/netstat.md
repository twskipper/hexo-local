---
title: '命令总结(二): netstat'
permalink: netstat
tags:
  - linux
  - shell
id: 434
categories:
  - Docs
date: 2016-01-10 00:15:36
---

netstat命令

  netstat命令的功能是现实网络连接,路由表和网络接口的信息，可以让用户得知目前都有哪些网络正在连接和显示网络链接的信息与ss命令相似。

常用命令:
``` bash
netstat -an
netstat -rn
netstat -tunlp
\##offen use
netstat -an|awk '/^tcp/ {++S[$NF]} END {for (a in S)print a,S[a]}'#统计TCP状态
```
参数说明:(netstat -h)

&nbsp; &nbsp; &nbsp; &nbsp; -r, --route &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;display routing table

&nbsp; &nbsp; &nbsp; &nbsp; -I, --interfaces=&lt;Iface&gt; &nbsp; display interface table for &lt;Iface&gt;&nbsp;

	&nbsp; &nbsp; &nbsp; &nbsp;	#解释直接natstat -I 现实所有接口的网络信息 使用--interfaces=&lt;Iface&gt; 显示指定网卡信息。

	<!--more-->

&nbsp; &nbsp; &nbsp; &nbsp; -i, --interfaces &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; display interface table

&nbsp; &nbsp; &nbsp; &nbsp; -g, --groups &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; display multicast group memberships

&nbsp; &nbsp; &nbsp; &nbsp; -s, --statistics &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; display networking statistics (like SNMP)#显示每个协议的统计信息

&nbsp; &nbsp; &nbsp; &nbsp; -M, --masquerade &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; display masqueraded connections

&nbsp; &nbsp; &nbsp; &nbsp; -v, --verbose &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;be verbose

&nbsp; &nbsp; &nbsp; &nbsp; -n, --numeric &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;don't resolve names#显示实际地址，而不是对地址的解释或显示主机

&nbsp; &nbsp; &nbsp; &nbsp; --numeric-hosts &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;don't resolve host names

&nbsp; &nbsp; &nbsp; &nbsp; --numeric-ports &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;don't resolve port names

&nbsp; &nbsp; &nbsp; &nbsp; --numeric-users &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;don't resolve user names

&nbsp; &nbsp; &nbsp; &nbsp; -N, --symbolic &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; resolve hardware names

&nbsp; &nbsp; &nbsp; &nbsp; -e, --extend &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; display other/more information

&nbsp; &nbsp; &nbsp; &nbsp; -p, --programs &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; display PID/Program name for sockets#常用现实进程的名称及pid

&nbsp; &nbsp; &nbsp; &nbsp; -c, --continuous &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; continuous listing

&nbsp; &nbsp; &nbsp; &nbsp; -l, --listening &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;display listening server sockets

&nbsp; &nbsp; &nbsp; &nbsp; -a, --all, --listening &nbsp; &nbsp; display all sockets (default: connected)

&nbsp; &nbsp; &nbsp; &nbsp; -o, --timers &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; display timers

&nbsp; &nbsp; &nbsp; &nbsp; -F, --fib &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;display Forwarding Information Base (default)

&nbsp; &nbsp; &nbsp; &nbsp; -C, --cache &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;display routing cache instead of FIB

&nbsp; &nbsp; &nbsp; &nbsp; -T, --notrim &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; stop trimming long addresses

&nbsp; &nbsp; &nbsp; &nbsp; -Z, --context &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp;display SELinux security context for sockets

&nbsp; &nbsp; &nbsp; &nbsp; &lt;Socket&gt;={-t|--tcp} {-u|--udp} {-S|--sctp} {-w|--raw} {-x|--unix} --ax25 --ipx --netrom

&nbsp;netstat -an参数中state(awk $NF)含义:

&nbsp;参考TCP的状态转换

&nbsp;State

&nbsp; &nbsp; &nbsp; &nbsp;The state of the socket. Since there are no states in raw mode and usually no &nbsp;states &nbsp;used

&nbsp; &nbsp; &nbsp; &nbsp;in UDP, this column may be left blank. Normally this can be one of several values:

&nbsp; &nbsp; &nbsp; &nbsp;ESTABLISHED

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; The socket has an established connection.#一个打开的链接数，总数即并发数

&nbsp; &nbsp; &nbsp; &nbsp;SYN_SENT

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; The socket is actively attempting to establish a connection.

&nbsp; &nbsp; &nbsp; &nbsp;SYN_RECV

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; A connection request has been received from the network.

&nbsp; &nbsp; &nbsp; &nbsp;FIN_WAIT1

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; The socket is closed, and the connection is shutting down.

&nbsp; &nbsp; &nbsp; &nbsp;FIN_WAIT2

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Connection &nbsp;is closed, and the socket is waiting for a shutdown from the remote end.

&nbsp; &nbsp; &nbsp; &nbsp;TIME_WAIT

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; The socket is waiting after close to handle packets still in the network.

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; #等待足够的时间来确保远程TCP接收到连接中断请求的确认

&nbsp; &nbsp; &nbsp; &nbsp;CLOSED The socket is not being used.

&nbsp; &nbsp; &nbsp; &nbsp;CLOSE_WAIT

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; The remote end has shut down, waiting for the socket to close.

&nbsp; &nbsp; &nbsp; &nbsp;LAST_ACK

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; The remote end has shut down, and the socket is closed. Waiting for acknowledgement.

&nbsp; LISTEN&nbsp;

&nbsp; &nbsp; &nbsp; &nbsp;		 &nbsp;The &nbsp;socket is listening for incoming connections. &nbsp;Such sockets are not included in the output unless you specify the --listening (-l) or --all (-a) option.

&nbsp; &nbsp; &nbsp; &nbsp;		 &nbsp;#监听来自远程主机的TCP端口的连接请求，服务器在等待进入呼叫

&nbsp; &nbsp; &nbsp; &nbsp;CLOSING

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; Both sockets are shut down but we still don’t have all our data sent.

&nbsp; &nbsp; &nbsp; &nbsp;UNKNOWN

&nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; The state of the socket is unknown.