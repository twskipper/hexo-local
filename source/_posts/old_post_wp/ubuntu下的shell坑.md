---
title: ubuntu下的shell坑
permalink: ubuntu-tips
tags:
  - shell
categories:
  - Docs
date: 2016-05-03 15:26:58
---

今天使用一个nginx日志切割脚本做日志切割工作，有一句定义log文件名数组的就是
``` plain
 log_files_name=(www.belle8.com nginx_error)
```
然后测试的时候使用sh 去执行总是不行报错Syntax error: “(” unexpected
因为我每次都是使用sh 去执行脚本
换成bash 去执行脚本就行了。
就是sh和bash还是存在差异的。