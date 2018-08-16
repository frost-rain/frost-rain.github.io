---
layout: post
title: "SQL注入原理 -万能密码注入"
description: "SQL注入原理 -万能密码注入"
tag: web 安全
---

<br />

---

<br />

## **实验目的:**

##### &nbsp;&nbsp;&nbsp;1.理解万能密码的原理

##### &nbsp;&nbsp;&nbsp;2.学习万能密码的使用

<br />

## **实验原理:**

##### &nbsp;&nbsp;&nbsp; 用户进行用户名和密码验证时，网站需要查询数据库。查询数据库就是执行SQL语句;

##### &nbsp;&nbsp;&nbsp; 针对此论坛，当用户登录时，后台执行的数据库查询操作（SQL语句）是 

<code>Select user_id,user_type,email From users Where user_id='用户名' And password='密码'</code>

##### &nbsp;&nbsp;&nbsp; 由于网站后台在进行数据库查询的时候没有没有对单引号进行过滤，当输入用户名【admin】和万能密码【2 'or' 1】时，执行的SQL语句为

<code>Select user_id,user_type,email From users Where user_id='admin' And password='2 'or' 1'</code>

##### &nbsp;&nbsp;&nbsp; 同时，由于SQL语句中逻辑运算符具有优先级，[=] 优于 [and], [and] 优于 [or]，且使用传递性。因此，此SQL语句在后台解析时，分成两句

<code>Select user_id,user_type,email From users Where user_id='admin' And password='2'</code>

<code>'1'</code>

##### &nbsp;&nbsp;&nbsp; 两句bool值进行逻辑or运算，恒为true。SQL的查询结果为true，意味着验证成功，也可以进入到系统当中。

<br />

## **实验步骤:**

<b>●</b>打开IE浏览器，输入<code>http://192.168.1.3:8001</code> 进入到下图网页当中

<img src="/files/SQL injection principle - universal password injection/1.png" width="400px" height="200">

<b>○</b>输入用户名【admin】，密码【1 'or' 2】即可登录系统

<br />

## **实验总结:**

这次的实验比较简单，但是由于有指导的情况下，万能密码显得很容易;

对于不同的环境，万能密码不一样，所以要多了解万能密码，尝试多种万能密码。









