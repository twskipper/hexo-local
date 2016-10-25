---
title: vim 配置tab为4个空格
permalink: vim-tab-4-space
tags:
  - linux
  - 优化
categories:
  - Docs
date: 2015-12-09 16:07:11
---

在用户目录下新建
``` bash
vim ~/.vimrc
```
添加以下代码后，重启vim即可实现按TAB产生4个空格
``` bash
set ts=4  
set expandtab
```
以后再文档里在详细研究vim的配置.