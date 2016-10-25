---
title: pip 更换aliyun的源
permalink: pip-use-aliyun-mirrors
tags:
  - linux
  - python
  - shell
categories:
  - Docs
date: 2015-12-16 13:54:02
---

 执行以下一条命令即可

 pip
<pre class="lang:sh decode:true " >mkdir $HOME/.pip 2&gt;/dev/null;printf "[global]\nindex-url=http://mirrors.aliyun.com/pypi/simple\n[install]\ntrusted-host=mirrors.aliyun.com" > $HOME/.pip/pip.conf</pre> 

easy_install

<pre class="lang:sh decode:true " >printf "[easy_install]\nindex-url=http://mirrors.aliyun.com/pypi/simple" &gt;$HOME/.pydistutils.cfg</pre> 