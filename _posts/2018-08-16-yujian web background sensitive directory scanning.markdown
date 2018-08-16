---
layout: post
title: "御剑web后台敏感目录扫描"
description: "御剑web后台敏感目录扫描"
tag: web 安全
---

<style>
.margin-left{
	margin-left:40px;
}
</style>

<br />

---

<br />

## **实验目的:**

##### &nbsp;&nbsp;&nbsp;1.了解御剑后台扫描工具

##### &nbsp;&nbsp;&nbsp;2.学习御剑后台扫描工具的使用

<br />

## **实验原理:**

##### &nbsp;&nbsp;&nbsp; 御剑扫描工具主要用来扫描目标站点的敏感目录，如后台管理界面，cms类型以及版本等。

<br />

## **实验步骤:**

<b>●</b>打开御剑web后台扫描工具，在域名的的框中输入目标站点的URL: <code>192.168.1.3:8001</code> ,点击开始扫描

<img src="/files/yujian web background sensitive directory scanning/1.png" width="500px" height="80px">

<br />

<b>○</b>扫描结果如下图，可双击链接打开网页,HTTP响应为200的链接都是可以访问的

<img src="/files/yujian web background sensitive directory scanning/2.png" width="500px" height="250px">

<br />

<b>●</b>双击URL: <code>http://192.168.1.3:8001 /admin/Login.asp</code> 可进入后台管理界面，可以通过SQL注入进入后台

<br />

<b>○</b>双击URL: <code>http://192.168.1.3:8001 /FCKeditor/_whatsnew.html</code> 即可知道该站点的编辑器类型为FCK及其版本号

<img src="/files/yujian web background sensitive directory scanning/3.png" width="500px" height="250px">

<br />

## **附加:**

<b>●</b>查看目标站点的数据库类型

<p class="margin-left">
1.双击URL: <code>http://192.168.1.3:8001 /admin/Login.asp</code> 进入后台管理界面
</p>

<p class="margin-left">
2.在进入的界面中可以看到数据库是Access
</p>

<img src="/files/yujian web background sensitive directory scanning/4.png" width="500px" height="250px">

<br />

## **实验总结:**

御剑web后台敏感目录扫描工具使用简便，但功能也受限;

一般来说，我们访问的网站不会对外显示后台管理界面与有关网站敏感信息的界面，通过这个工具进行扫描，可以找出目标站点敏感目录，如文件上传界面，甚至是网站的源代码，获取有用的信息后，我们可能可以通过其获取后台管理权限或是查看后台数据库;

因为它功能受限，所以可以搭配其它的工具进行使用。








