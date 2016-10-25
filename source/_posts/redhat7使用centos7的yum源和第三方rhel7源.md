---
title: redhat7使用centos7的yum源和第三方rhel7源
permalink: redhat-use-centos-yum
id: 49
categories:
  - Docs
date: 2015-10-19 19:58:52
tags:
  - config
  
---

1、搜索redhat的yum软件包
<pre class="lang:default decode:true ">rpm -e yum 软件包名称</pre>
2、卸载这些软件包
<pre class="lang:default decode:true ">rpm -e yum 软件包名称</pre>
3、找到centos下得yum包。注意*号，代表版本号，自行替换

进入 /usr/local/src/

<!--more-->

下载
<pre class="lang:default decode:true ">[root@localhost ~]# wget https://mirrors.aliyun.com/centos/7/os/x86_64/Packages/yum-*.centos.noarch.rpm
[root@localhost ~]# wget https://mirrors.aliyun.com/centos/7/os/x86_64/Packages/yum-metadata-parser-*.rpm
[root@localhost ~]# wget https://mirrors.aliyun.com/centos/7/os/x86_64/Packages/yum-utils-*.noarch.rpm
[root@localhost ~]# wget https://mirrors.aliyun.com/centos/7/os/x86_64/Packages/yum-updateonboot-*.noarch.rpm
[root@localhost ~]# wget https://mirrors.aliyun.com/centos/7/os/x86_64/Packages/yum-plugin-fastestmirror-*.noarch.rpm</pre>
4、安装这些yum软件包
<pre class="lang:default decode:true ">rpm -ivh yum-*</pre>
5、下载centos源
<pre class="wrap:true lang:default decode:true ">wget -O /etc/yum.repos.d/CentOS-Base.repo https://mirrors.aliyun.com/repo/Centos-7.repo</pre>
6、下载第三方redhat源
<pre class="wrap:true lang:default decode:true ">yum -y install epel-release &amp;amp;&amp;amp; rpm -Uvh https://li.nux.ro/download/nux/dextop/el7/x86_64/nux-dextop-release-0-1.el7.nux.noarch.rpm</pre>