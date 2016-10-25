title: aliyun 使用 ubuntu 16.04镜像
date: 2016/10/24 21:52:20
description: 阿里云使用ubuntu16.04镜像的方法。
categories: Docs
tags:
  - config
  - linux
permalink: aliyun-ubuntu-xenial
---

#### aliyun获取ubuntu16.04

*截止到2016年阿里云还没在ECS新建实例里提供Ubuntu16.04版本*
因为最近docker的发展，很多新东西都是使用ubuntu16.04.
比如kubernetes.io 里面的guides 使用的ubuntu16.04，其实 14.04也行。

废话不多说。在阿里云使用ubuntu16.04 LTS版本目前我就知道一种
先购买一台使用ubuntu 14.04镜像的ECS，然后升级到16.04，如果机器很多，可以一台升级，然后做
成自定义镜像。这样以后都可以直接部署了。和VM一样。

*那么问题来了，怎么升级呢*
**Easy！**
1, 先更新系统保证更新过程不出错。（依赖问题）
``` bash
apt update \
&& apt dist-upgrade
```
2, 然后使用screen -S update 新建个screen
``` bash
screen -S update
```
3, 升级！ (保障有外网哦)
\#TIPS 可以删除/etc/apt/source.list.d/sources-aliyun-1.list 或者改名非.list
\# 这样可以使用阿里云提供的内网镜像仓库，加快速度。
*GO!*
``` bash
do-release-upgrade
```
##### 一路上YES YES YES 回车回车就行。 也可以根据提示自己判断。升级完成后（20分钟左右。）
##### 重启后，检查没问题就可以创建自定义镜像
[自定义镜像官网指导](https://help.aliyun.com/knowledge_detail/40549.html)

## 搞定。
@skipper
