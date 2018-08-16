---
layout: post
title: "APPscan扫描器扫描web漏洞"
description: "APPscan扫描器扫描web漏洞"
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

##### &nbsp;&nbsp;&nbsp;1.了解APPscan扫描器

##### &nbsp;&nbsp;&nbsp;2.学习APPscan的用法

<br />

## **实验原理:**

##### &nbsp;&nbsp;&nbsp; Rational AppScan (简称AppScan)其实是一一个产品家族，包括众多的应用安全扫描产品;

##### &nbsp;&nbsp;&nbsp; 从开发阶段的源代码扫描的AppScan sourceedition,到针对Web应用进行快速扫描的AppScan standardedition,以及进行安全管理和汇总整合的AppScan enterprise Edition等。我们经常说的AppScan就是指的桌面版本的AppScan,即AppScan standard edition。其安装在Windows操作系统上，可以对网站等Web应用进行自动化的应用安全扫描和测试;

##### &nbsp;&nbsp;&nbsp; AppScan工作原理小结如下:

##### &nbsp;&nbsp;&nbsp; 通过搜索(爬行)发现整个Web应用结构;

##### &nbsp;&nbsp;&nbsp; 根据分析，发送修改的HTTP Request进行攻击尝试(扫描规则库)通过对于Respone的分析验证是否存在安全漏洞。


<br />

## **实验步骤:**

<b>●</b>打开APPscan，单击文件，新建

<img src="/files/APPscan scanner scans for web vulnerabilities/1.png" width="400px" height="150px">

<br />

<b>○</b>选择要扫描的模板，此处选常规扫描即可

<img src="/files/APPscan scanner scans for web vulnerabilities/2.png" width="300px" height="150px">

<br />

<b>●</b>进入扫描向导，选择web应用程序扫描

<img src="/files/APPscan scanner scans for web vulnerabilities/3.png" width="300px" height="150px">

<br />

<b>○</b>下一步，填入目标站点的URL: <code>192.168.1.3:8001</code> 

<img src="/files/APPscan scanner scans for web vulnerabilities/4.png" width="300px" height="150px">

<br />

<b>●</b>进入选择登录方法界面，默认即可，在弹出窗口中点是

<img src="/files/APPscan scanner scans for web vulnerabilities/5.png" width="300px" height="150px">

<br />

<b>○</b>测试策略选择缺省值 default

<img src="/files/APPscan scanner scans for web vulnerabilities/6.png" width="300px" height="150px">

<br />

<b>●</b>选择扫描方式“启动全面扫描”，点击完成跳出“自动保存”的选择框，选择是

<img src="/files/APPscan scanner scans for web vulnerabilities/7.png" width="300px" height="150px">

<img src="/files/APPscan scanner scans for web vulnerabilities/8.png" width="250px" height="100px">

<br />

<b>○</b>程序自动启动“扫描专家”，扫描结束后点击应用建议

<img src="/files/APPscan scanner scans for web vulnerabilities/9.png" width="500px" height="100px">

<br />

<b>●</b>等待很久之后扫描完成，扫描结果如下图。若想保存结果，点击工具栏中的报告

<img src="/files/APPscan scanner scans for web vulnerabilities/10.png" width="300px" height="150px">

<br />

## **实验总结:**

APPscan的漏洞扫描比AWVS扫描器强大，但是耗时也很长;

对于APPscan的扫描结果，几乎看不懂，有必要多了解数据库及web相关知识

对于这些工具，要多加使用练练熟练度;

同时，有机会的话，了解一下这些工具扫描漏洞的原理。









