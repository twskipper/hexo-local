---
title: CentOS安装开发环境
tags:
  - linux
  - 配置
id: 299
categories:
  - linux
  - 配置
date: 2015-12-16 09:30:46
---

<pre class="lang:sh decode:true ">包括gcc 开发库，为以后编译各种软件做准备

yum groupinstall "Compatibility libraries" "Base" "Development tools" -y

yum groupinstall "debugging Tools" "Dial-up Networking Support" -y</pre>
&nbsp;