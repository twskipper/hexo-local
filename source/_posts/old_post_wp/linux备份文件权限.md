---
title: linux备份文件权限
tags:
  - linux
  - Tips
categories:
  - Docs
date: 2015-12-01 23:25:25
permalink: linxu-backup-your-rights
---

备份文件权限

umount 所有不需要被处理的设备，例如NTFS/FAT 这类不能保存权限的分区，可能的话也umount 你的home（~），然后使用getfacl 保存所有文件的权限，例如

<pre class="lang:default decode:true " >sudo getfacl -R / &gt;sysfacl-root-$(date +%Y-%m-%d).facl </pre>

保管好这个权限存档文件，有朝一日手滑之后你会想起来它的。
恢复文件权限

<!--more-->

同样umount 所有不需要被处理的设备，然后从文件权限备份中批量恢复权限

<pre class="lang:default decode:true " >sudo setfacl --restore=ur_facl_bak_file</pre>

没了，有效防止chmod -R 755 /etc 之类的灾难。
制约危险指令

自不必说的首先就是 chmod 和 rm 这两个危险指令应该尽量受到制约，它们90% 悲剧的源头

<pre class="lang:default decode:true " >
alias chmod='/usr/bin/env chmod --preserve-root'
alias rm='/usr/bin/env rm -I --preserve-root'
</pre>

然而实质性的东西并没有改变，《UNIX痛恨者手册》中就花了很大的篇幅来批评 rm 这类不负责任的指令。Linux 把这些都一股脑推给了用户，然而并没有多少用户愿意去封装这些指令，或者干脆做一个更加安全的实现。这些原始的指令仍然被高频率使用。
类似的，你或许还要 alias 一些其他的指令：

<pre class="lang:default decode:true " >alias cp='/usr/bin/env cp -i'
alias mv='/usr/bin/env mv -i'
alias ln='/usr/bin/env ln -i'
alias chown='/usr/bin/env chown --preserve-root'
alias chgrp='/usr/bin/env chgrp --preserve-root'</pre>

原帖
[http://blog.csdn.net/ispeller/article/details/45534323](http://blog.csdn.net/ispeller/article/details/45534323)
