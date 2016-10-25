---
title: os x 挂载远程（不同网段)nfs
permalink: osx-nfs
tags:
  - OSX
categories:
  - Docs
date: 2015-10-30 10:33:25
---

关于NFS服务器的配置，这里就不写了网上一大堆。
这里说一下/etc/exports的配置

*需要在exports文件中添加insecure选项，表示接受>1024端口来的请求。因为一般路由器采用动态NAT会使用10000以上端口号连接。*
``` bash
vim /etc/exports
/需要共享的目录 (rw,no_root_squash,no_all_squash,insecure)
chmod /需要共享的目录 777 权限自己斟酌
```
OS X 配置
```
sudo -s
```
输入密码,或者
```
sudo mount -t nfs -o resvport ip:/共享目录 /OSx的目录
```

关于开机启动
编写个autonfs.sh
将挂载命令复制进去

保存
```
chmod a+x autonfs.sh
cd /Library/LaunchDaemons
```
vi autonfs.plist

<pre class="theme:terminal toolbar:1 lang:default decode:true " >&lt;?xml version="1.0" encoding="UTF-8"?&gt;
&lt;!DOCTYPE plist PUBLIC "-//Apple Computer//DTD PLIST 1.0//EN"
    "http://www.apple.com/DTDs/PropertyList-1.0.dtd"&gt;
&lt;plist version="1.0"&gt;
&lt;dict&gt;
    &lt;key&gt;Label&lt;/key&gt;
        &lt;string&gt;autonfs&lt;/string&gt;
    &lt;key&gt;UserName&lt;/key&gt;
        &lt;string&gt;root&lt;/string&gt;
    &lt;key&gt;ProgramArguments&lt;/key&gt;
    &lt;array&gt;
         &lt;string&gt;/Users/skipper/Documents/autonfs.sh&lt;/string&gt;#写你脚本的绝对路径
         &lt;string&gt;run&lt;/string&gt;
    &lt;/array&gt;
    &lt;key&gt;RunAtLoad&lt;/key&gt;
    &lt;true/&gt;
&lt;/dict&gt;
&lt;/plist&gt;         </pre> 