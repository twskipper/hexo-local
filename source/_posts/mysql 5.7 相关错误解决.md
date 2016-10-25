---
title: mysql 5.7 相关错误解决
tags:
  - mysql
id: 584
comment: false
categories:
  - 排错
date: 2016-08-29 14:31:08
---

在使用备份工具备份到时候报错

Table 'performance_schema.session_variables' doesn't exist

解决方法

使用root账户登录

mysql&gt; set @@global.show_compatibility_56=ON;

搞定！