---
title: 修复因为dpkg 导致的apt-get无法安装软件
permalink: dpkg-rescure
tags:
  - 排错
  - linux
id: 543
categories:
  - Docs
date: 2016-05-06 13:53:50
---

 2条命令搞定。
 ``` bash
sudo aptitude update   
sudo aptitude -f install
```

感谢[http://blog.csdn.net/ling1874/article/details/5733883](http://blog.csdn.net/ling1874/article/details/5733883)