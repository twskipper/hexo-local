---
title: mysql单实例安装配置
tags:
  - linux
  - mysql
  - 配置
id: 308
categories:
  - linux
  - mysql
  - 配置
date: 2015-12-16 10:58:09
---

mysql发布的版本
alpha beta RC GA

升级版本过程
先评估版本，导出SQL，安装新版本，导入SQL

主流版本
5.5
选择版本
选择发布6个月左右的没有大的bug修复的GA版本
mysql安装方法
1，yum
对mysql要求不太高的公司使用
*大公司将编译好的软件打包成rpm包，搭建yum仓库，
2，常规方式编译安装
3，**采用cmake方式编译安装MYSQL
4采用二进制方式免编译安装MySQL
cmake方法介绍
<!--more-->

cmake软件
<pre class="lang:sh decode:true ">wget http://file.inpeace.cn/sqllearn/cmake-2.8.8.tar.gz
tar xf cmake-2.8.8.tar.gz
cd cmake-2.8.8
./configure</pre>
等输出以下结果的时候
bootstrapped. Now run gmake.
执行
<pre class="lang:sh decode:true  ">make &amp;&amp; make install
完成后执行
cd ../</pre>
准备编译mysql5.5
<pre class="lang:sh decode:true ">**依赖包
yum install ncurses-devel -y

下载mysql5.5
wget http://file.inpeace.cn/sqllearn/mysql-5.5.32.tar.gz</pre>
创建用户和组
<pre class="lang:sh decode:true ">groupadd mysql
useradd mysql -s /sbin/nologin -M -g mysql</pre>
解压编译MySQL
<pre class="lang:sh decode:true ">tar zxf mysql-5.5.32.tar.gz
cd mysql-5.5.32

cmake . -DCMAKE_INSTALL_PREFIX=/apps/mysql-5.5.32 \
-DMYSQL_DATADIR=/apps/mysql-5.5.32/data \
-DMYSQL_UNIX_ADDR=/apps/mysql-5.5.32/tmp/mysql.sock \
-DDEFAULT_CHARSET=utf8 \
-DDEFAULT_COLLATION=utf8_general_ci \
-DEXTRA_CHARSETS=gbk,gb2312,utf8,ascii \
-DENABLED_LOCAL_INFILE=ON \
-DWITH_INNOBASE_STORAGE_ENGINE=1 \
-DWITH_FEDERATED_STORAGE_ENGINE=1 \
-DWITH_BLACKHOLE_STORAGE_ENGINE=1 \
-DWITHOUT_EXAMPLE_STORAGE_ENGINE=1 \
-DWITHOUT_PARTITION_STORAGE_ENGINE=1 \
-DWITH_FAST_MUTEXES=1 \
-DWITH_ZLIB=bundled \
-DENABLED_LOCAL_INFILE=1 \
-DWITH_READLINE=1 \
-DWITH_EMBEDDED_SERVER=1 \
-DWITH_DEBUG=0</pre>
编译安装
<pre class="lang:sh decode:true ">make &amp;&amp; make install</pre>
设置环境变量
<pre class="lang:sh decode:true ">echo 'export PATH="/apps/mysql-5.5.32/bin:$PATH"' &gt;&gt;/etc/profile
source /etc/profile</pre>
链接
<pre class="lang:sh decode:true ">ln -s /apps/mysql-5.5.32 /apps/mysql
</pre>
权限
<pre class="lang:sh decode:true ">chown -R mysql:mysql /apps/mysql-5.5.32/
chmod -R 1777 /tmp/
</pre>
标准单实例
初始化
<pre class="lang:sh decode:true ">cd /apps/mysql/scripts/
./mysql_install_db --basedir=/apps/mysql --datadir=/apps/mysql/data/ --user=mysql
</pre>
初始化成功的输出：
<pre class="lang:sh decode:true ">To start mysqld at boot time you have to copy
support-files/mysql.server to the right place for your system

PLEASE REMEMBER TO SET A PASSWORD FOR THE MySQL root USER !
To do so, start the server, then issue the following commands:
**
/apps/mysql/bin/mysqladmin -u root password 'new-password'
/apps/mysql/bin/mysqladmin -u root -h mysql password 'new-password'

Alternatively you can run:
/apps/mysql/bin/mysql_secure_installation

which will also give you the option of removing the test
databases and anonymous user created by default. This is
strongly recommended for production servers.

See the manual for more instructions.

You can start the MySQL daemon with:
cd /apps/mysql ; /apps/mysql/bin/mysqld_safe &amp;amp;

You can test the MySQL daemon with mysql-test-run.pl
cd /apps/mysql/mysql-test ; perl mysql-test-run.pl</pre>
复制配置文件
<pre class="lang:sh decode:true ">cp /apps/mysql/support-files/my-small.cnf /etc/my.cnf</pre>
复制启动脚本
<pre class="lang:sh decode:true ">cp /apps/mysql/support-files/mysql.server /etc/init.d/mysqld</pre>
添加权限
<pre class="lang:sh decode:true ">chmod +x /etc/init.d/mysqld</pre>
启动
<pre class="lang:sh decode:true ">/etc/init.d/mysqld start</pre>
设置开机启动
<pre class="lang:sh decode:true ">chkconfig mysqld on</pre>
查看端口
<pre class="lang:sh decode:true ">netstat -tunlp|grep 3306
lsof -i :3306</pre>