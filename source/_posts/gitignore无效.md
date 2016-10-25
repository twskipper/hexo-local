---
title: .gitignore忽略规则以及不生效的方法(转)
tags:
  - git
id: 624
comment: false
categories:
  - OSX
  - 配置
date: 2016-09-13 11:11:20
---

在git中如果想忽略掉某个文件，不让这个文件提交到版本库中，可以使用修改根目录中 .gitignore 文件的方法（如无，则需自己手工建立此文件）。这个文件每一行保存了一个匹配的规则例如：
<pre class="lang:default decode:true">*.a # 忽略所有 .a 结尾的文件
!lib.a # 但 lib.a 除外
/TODO # 仅仅忽略项目根目录下的 TODO 文件，不包括 subdir/TODO
build/ # 忽略 build/ 目录下的所有文件
doc/*.txt # 会忽略 doc/notes.txt 但不包括 doc/server/arch.txt</pre>
有时候在项目开发过程中，**突然心血来潮想把某些目录或文件加入忽略规则，按照上述方法定义后发现并未生效，**

原因是**.gitignore只能忽略那些原来没有被track的文件。**

如果某些文件已经被纳入了版本管理中，则修改.gitignore是无效的。那么解决方法就是先把本地缓存删除（改变成未track状态），然后再提交：
<pre class="lang:default decode:true ">git rm -r --cached .

git add .

git commit -m "update .gitignore"</pre>
&nbsp;

[原贴链接](http://www.pfeng.org/archives/840)