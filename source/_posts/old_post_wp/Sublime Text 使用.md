title: Sublime Text 使用
date: 2016-10-23 14:00:13
tags:
  - OSX
categories: Docs
permalink: sublime-text
description: Sublime Text 3的一些使用文档。
---

## 下载安装 Sublime Text
[google 知道](https://www.google.com)
官网导航[Sublime Text 3](http://www.sublimetext.com/3)
### 安装Package Control
官网传送门 [install](https://packagecontrol.io/installation)

#### sublime-text 3 安装 Package Control
以OS X为例子，打开sublime text 3 按住control + ~
输入以下内容 ##tips: 在代码上面三连击鼠标 左键就可以选择改行。复制了。
``` python
import urllib.request,os,hashlib; h = 'df21e130d211cfc94d9b0905775a7c0f' + '1e3d39e33b79698005270310898eea76'; pf = 'Package Control.sublime-package'; ipp = sublime.installed_packages_path(); urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) ); by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); dh = hashlib.sha256(by).hexdigest(); print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)

```
#### 完成后就可以command + shift + p 然后输入 PPIP 不是PPAP
   打开PPIP 后输入ChineseLocalization 安装后就可以用中文了。
为了对中文文档的支持，还要安装ConvertToUTF8 这个插件
#### tips
1, 使用命令行工具
``` bash
ln -s /Applications/Sublime\ Text.app/Contents/SharedSupport/bin/subl /usr/local/bin/subl
```
使用方法也简单
``` bash
subl filename
```
##自己用的插件
