---
layout: post
title: "安装MySQL"
description: "安装MySQL"
tag: MySQL
---

<style>
#padding{
padding-left:68px
}
#pre{
margin-left:68px;
width:85%;
}
</style>

<br />

**概述**
---
---

MySQL 是最流行的关系型数据库管理系统，在WEB应用方面 MySQL 是最好的RDBMS(Relational Database Management System：关系数据库管理系统)应用软件之一。

虽然现在Google、Mozilla、Adobe等公司都在使用NoSQL,但是MySQL依然有其不可替代的优势，依然在数据库中保持着领先地位。

所有平台的MySQL的安下载地址:
<a href="https://dev.mysql.com/downloads/mysql/" target="blank">MySQL下载</a>

<p style="color:firebrick">注意:安装过程需要管理员权限，否则会因权限不足导致安装失败</p>

<br />

**Windows**
---
---
<p style="text-align:right;font-size:120%">
<a href="https://dev.mysql.com/doc/refman/8.0/en/windows-install-archive.html" target="blank">
参考:MySQL官网英文文档
</a>
</p>

<br />

1.&nbsp; 在官网中下载Windows版本的zip包，并解压到相应的目录(自己想放哪就放哪)，这里我将文件夹放于 <code>D:\Program Files\mysql-8.0.12</code> 中

<br />

2.&nbsp; 配置MySQL的配置文件

<p id="padding">
<b>●</b>打开刚刚解压的文件夹，里面可能有自带的配置文件 <code>my-default.ini</code> ,不管有没有，在文件夹内新建一个名为 <code>my.ini</code> 的文件
</p>

<br />

<p id="padding">
<b>○</b>编辑 <code>my.ini</code> 配置以下基本信息(用记事本打开即可)
</p>

<pre id="pre">
<code class="language-cmd hljs cpp" >
[mysql]
#设置mysql客户端默认字符集
default-character-set=utf8

[mysqld]
#设置3306端口
port = 3306
#设置mysql的安装目录
basedir=D:\\Program Files\mysql-8.0.12
#设置mysql数据库的数据的存放目录
datadir=E:\\repository\mysql-data
# 允许最大连接数
max_connections=20
#服务端使用的字符集默认为8比特编码的latin1字符集
character-set-server=utf8
#创建新表时将使用的默认存储引擎
default-storage-engine=INNODB
</code>
</pre>

<p id="padding">
<b style="color:firebrick">注意:basedir与datadir后面的斜杠数量一定得注意</b>
</p>

<div id="padding">
<code>D:\\Program Files\mysql-8.0.12</code>
<br />
<code>D:\\Program Files\\mysql-8.0.12</code>
</div>

<p id="padding">
以上都是可用的，下面这个反斜杠方式一定不能用，会报错
</p>

<div id="padding">
<code>D:\Program Files\mysql-8.0.12</code>如果出现下面的报错，考虑是否是因为斜杠的原因
</div>

<pre id="pre">
<code class="language-cmd hljs cpp" >
PS D:\Program Files\mysql-8.0.12\bin> .\mysqld --initialize-insecure
2018-08-20T10:59:10.353137Z 0 [System] [MY-013169] [Server] D:\Program Files\mysql-8.0.12\bin\mysqld.exe (mysqld 8.0.12) initializing of server in progress as process 10204
2018-08-20T10:59:10.355624Z 0 [ERROR] [MY-010457] [Server] --initialize specified but the data directory has files in it. Aborting.
2018-08-20T10:59:10.361854Z 0 [ERROR] [MY-010119] [Server] Aborting
2018-08-20T10:59:10.364597Z 0 [System] [MY-010910] [Server] D:\Program Files\mysql-8.0.12\bin\mysqld.exe: Shutdown complete (mysqld 8.0.12)  MySQL Community Server - GPL.
</code>
</pre>

<br />

3.&nbsp; 安装并启动MySQL

<div id="padding">
<b>●</b>以管理员身份运行cmd或powershell，切换目录到安装目录的bin文件夹内
<br />
<code>cd D:\Program Files\mysql-8.0.12\bin</code>
</div>

<br />

<p id="padding">
<b>○</b>输入安装命令
<br />
<code>mysqld install</code>(需要配置环境变量) 或 <code>.\mysqld install</code>
</p>

<br />

<div id="padding">
<b>●</b>初始化data目录: <code>mysqld --initialize-insecure</code>(若不行，加 .\ )
</div>

<br />

<p id="padding">
<b>○</b>启动MySQL: <code>net start mysql</code>
</p>

<br />

4.&nbsp; 添加环境变量

<p id="padding">
<b>●</b>右键此电脑->属性->高级系统设置->环境变量->双击下方系统变量一栏的PATH->编辑
</p>

<br />

<div id="padding">
<b>○</b>将安装目录的bin文件夹加入PATH中，此处我的为
<br />
<code>D:\Program Files\mysql-8.0.12\bin</code> 添加确定即可
</div>

<br />

5.&nbsp; 至此，win下的MySQL基本配置完成

<br />

**Linux**
---
---
<p style="text-align:right;font-size:120%">
<a href="https://dev.mysql.com/doc/mysql-apt-repo-quick-guide/en/" target="blank">
参考:MySQL官网英文文档
</a>
</p>

<br />

<p style="color:firebrick">这里以Ubuntu为例</p>

<br />

1.&nbsp; 打开终端，输入命令 <code>sudo apt-get install mysql-server mysql-client</code> 等待安装完成

<br />

2.&nbsp; 配置MySQL的配置文件

<div id="padding">
<b>●</b>MySQL的配置文件: <code>/etc/mysql/my.cnf</code> ,以root权限打开文件可见有以下两行
<br />
<br />
<code>!includedir /etc/mysql/conf.d/</code>
<br />
<code>!includedir /etc/mysql/mysql.conf.d/</code>
<br />
这说明在上面两个目录当中有 mysql 及 mysqld 的配置文件
</div>

<br />

<div id="padding">
<b>○</b>打开以下两个文件(root权限)
<br />
<code>/etc/mysql/conf.d/mysql.cnf </code> (mysql客户端的配置)
<br />
<code>/etc/mysql/mysql.conf.d/mysqld.cnf</code>(mysql服务器的配置)
</div>

<br />

<p id="padding">
<b>●</b>在<code>/etc/mysql/conf.d/mysql.cnf </code> 的<code>[mysql]</code>下添加以下内容
</p>

<pre id="pre">
<code class="language-cmd hljs cpp" >
[mysql]
#设置mysql客户端默认字符集
default-character-set=utf8
</code>
</pre>

<br />

<p id="padding">
<b>○</b>在<code>/etc/mysql/mysql.conf.d/mysqld.cnf </code> 的<code>[mysqld]</code>下添加以下没有的内容(或者更改)
</p>

<pre id="pre">
<code class="language-cmd hljs cpp" >
[mysqld]
#设置3306端口
port = 3306
#设置mysql的安装目录
basedir=/usr
#设置mysql数据库的数据的存放目录
datadir=/var/lib/mysql
# 允许最大连接数
max_connections=20
#服务端使用的字符集默认为8比特编码的latin1字符集
character-set-server=utf8
#创建新表时将使用的默认存储引擎
default-storage-engine=INNODB
</code>
</pre>

<br />

3.&nbsp; 查看、停止、开启MySQL server服务

<p id="padding">
<b>●</b>查看MySQL运行状态: <code>sudo service mysql status</code>
</p>

<br />

<p id="padding">
<b>○</b>停止: <code>sudo service mysql stop</code>
</p>

<br />

<p id="padding">
<b>●</b>开启: <code>sudo service mysql start</code>
</p>

<br />

4.&nbsp; Ubuntu下的MySQL安装完毕



























