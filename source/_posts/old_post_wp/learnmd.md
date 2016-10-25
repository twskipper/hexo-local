title: ready to use markdown
toc: ture
date: 2013/7/13 20:34:20
description: this is a md
---


# Heading I
``` bash
$ curl -u skipper:iskipper file.inpeace.cn
```

## Heading 2
*learn markdown is very important*


#####heading 4


## 架构优点
*	部署更加方便简单
*	维护更快速
*	可以重复使用

#### docker run demo
``` bash
	docker run -d restart=always \
	-p 80:80 \
	-p 443:443 \
	-v /webconf:/home/belle8/webconf/vhost \
	--volumes-from phpenv \
	--name nginx \
	nginx:1.10
```
#### 非常简单的启动
More info: [Blog](https://www.inpeace.cn)
