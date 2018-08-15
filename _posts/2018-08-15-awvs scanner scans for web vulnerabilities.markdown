---
layout: post
title: "awvs扫描器扫描web漏洞"
description: "awvs扫描器扫描web漏洞"
tag: web安全
---

<br />

---

<br />

## **实验目的:**

##### &nbsp;&nbsp;&nbsp;1.了解AWVS--web扫描工具

##### &nbsp;&nbsp;&nbsp;2.学习AWVS的用法

<br />

## **实验原理:**

##### &nbsp;&nbsp;&nbsp; AWVS（Acunetix Web VuInerrability Scanner）简介

##### &nbsp;&nbsp;&nbsp; WVS(Web Vulnerability Scanner)是一个自由化的Web立用程序安全测试工具,它可以扫描任何可通过Web浏览器方向的和遵循HTTP/HTTPS规则的Web站点和Web应用程序。

##### &nbsp;&nbsp;&nbsp; 适用于任何中小型和大型企业和其它人员的Web网站。WVS可以通过检查SQL注入攻击漏洞、跨站脚本攻击漏洞等来审核Web应用程序的安全性。 它可以扫描任何可通过Web浏览器彷向的和遵循HTTP/HTTPS规则的Web站点和Web应用程序。


<br />

## **实验步骤:**

<b>●</b> 单击工具栏中的"new scan",打开站点扫描向导;

输入实验所用URL地址 <code>http://192.168.1.3:8001</code> 如图:

<img src="/files/awvs scanner scans for web vulnerabilities/1.png" width="500px" height="250px">

<br />

<b>○</b>软件自动识别目标站点信息，也可手动修改已知选项

<img src="/files/awvs scanner scans for web vulnerabilities/2.png" width="300px" height="200px" > 

<br />

<b>●</b>进入"Crawling Options",默认即可

<img src="/files/awvs scanner scans for web vulnerabilities/3.png" width="300px" height="200px" > 

<br />

<b>○</b>选择扫描模板，一般选"default"即可

<img src="/files/awvs scanner scans for web vulnerabilities/4.png" width="300px" height="200px" > 

<br />

<b>●</b>如果网站需要登录，则在下图所示界面中添加登录信息，但是实验环境不需要登录

<img src="/files/awvs scanner scans for web vulnerabilities/5.png" width="300px" height="200px" > 

<br />

<b>○</b>最后再次进行信息确认，无误"finish"即可，等待一段时间扫描完成

<img src="/files/awvs scanner scans for web vulnerabilities/6.png" width="300px" height="200px" > 

<img src="/files/awvs scanner scans for web vulnerabilities/7.png" width="500px" height="250px" > 

<br />

## **附加:**

<b>●</b>"Site Crawler",爬虫功能，遍历站点目录结构，点击"tools"中的"Site Crawler",输入URL，start，结果如图


<img src="/files/awvs scanner scans for web vulnerabilities/8.png" width="500px" height="250px" > 

<img src="/files/awvs scanner scans for web vulnerabilities/9.png" width="500px" height="250px" > 

<br />

<b>○</b>"Target Finder",端口扫描，找出web服务器，自行添加8001，8080端口

<img src="/files/awvs scanner scans for web vulnerabilities/10.png" width="500px" height="250px" >

<br />

## **实验总结:**

在实验之前，看过一些教学视频，对web漏洞有个大概了解了;

这次实验主要练习了一下AWVS--web扫描工具的基本用法，对AWVS有初步了解;

实验环境中的AWVS版本过低，于是去网上找了新版的看了下，对比其它的web漏洞扫描器，觉得AWVS不够好(其实是因为它收费);

接下来做其他的实验了解其它的web漏洞扫描器，试试kali中的web漏洞扫描工具。
