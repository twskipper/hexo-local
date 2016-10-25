title: hexo博客里使用图片方法
date: 2016/10/25 14:35:20
description: hexo markdown使用图片并部署到服务器
categories: Docs
Tags:
  - config
  - markdown
permalink: markdown-img0
---

#### hexo 图片的问题如何

* 在主题根目录的source目录下*新建个目录* **s**
* 复制图片进去改好名字
* 在markdown里面使用图片


#### 下面的的图片代码如下注意是..s/x.jpg
``` plain
![OVERPIGU](../s/pigu.jpg)
```
![OVERPIGU](../s/pigu.jpg)

**搞定**
然后使用rsync方式部署到nginx服务器就行了。
至于使用git的方式应该没问题吧




