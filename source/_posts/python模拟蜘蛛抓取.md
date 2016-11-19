title: python模拟蜘蛛抓取网页
date: 2016/11/18 19:20:20
description: python模拟蜘蛛抓取网页，获得抓取的结果，判断针对不同蜘蛛的规则是否生效。
categories: Codes
tags:
  - python
  - spider
permalink: python_spider_like0
---

   最近维护discuz论坛，出现安全事件，利用discuz漏洞修改程序文件。篡改搜索引擎抓取的规则
具体就当检测到蜘蛛的时候跳转页面到指定非法网页。从而劫持流量。非常恶心。对于运维人员。在开发人员
忙着修补漏洞的时候。只能通过小小的程序。模拟抓取，如果有问题，报警，并且执行相关恢复工作。

核心的功能就是利用python请求页面然后修改http Header里的User-agent字段的值。就是UA，冒充搜索引擎。然后获取结果，在做些判断。用到的模块urllib2 python2.7
核心程序.
#### 核心代码
``` python
import urllib2
import sys
import os

def download(uri, user_agent):
    print 'downloading %s', uri
    headers = {'User-agent': user_agent}
    request = urllib2.Request(uri, headers=headers)
    html = urllib2.urlopen(request).read()
    return html

argv1 = sys.argv[1]
url = 'http://' + argv1

### 这个是获取终端标准输出重定向到文件。
f_handler = open('s.html', 'w')
sys.stdout = f_handler

print url
spider1 = 'Sogou web spider/4.0(+http://www.sogou.com/docs/help/webmasters.htm#07'
spider2 = 'Baiduspider'
spider3 = 'ok'
a = download(url, spider2)

print a
os.system('subl s.html') ## 这个是使用系统获取结果后自动用sublime 打开
```

保存文件名为spider.py
``` bash
touch s.html
python spider.py www.mufen.me
```
#### 具体蜘蛛的UA可以轻易获得，比如使用百度自己robots.txt文件
传送门:[百度robots.txt](https://www.baidu.com/robots.txt)

#### skipper
