---
layout: post
title: "SQL注入原理-手工注入access数据库"
description: "SQL注入原理-手工注入access数据库"
tag: web 安全
---

<style>
.margin-left{
	margin-left:40px
}
</style>

<br />

---

<br />

## **实验目的:**

##### &nbsp;&nbsp;&nbsp;1.理解SQL注入的原理

##### &nbsp;&nbsp;&nbsp;2.学习手工注入的过程

<br />

## **实验原理:**

##### &nbsp;&nbsp;&nbsp; 所谓SQL注入，就是通过把SQL命令插入到Web表单提交或输入域名或页面请求的查询字符串，最终达到欺骗服务器执行恶意的SQL命令;
##### &nbsp;&nbsp;&nbsp; 首先，在以 <code>.asp?id=32 (数字任意)</code> 结尾的链接依次添加语句 <code>'</code> 、 <code>and 1=1</code> 和<code>and 1=2</code>，来判断网站是否存在注入点;
##### &nbsp;&nbsp;&nbsp; 然后，添加语句<code>and exists(select * from admin)</code> ,根据页面返回结果来猜解表名;
##### &nbsp;&nbsp;&nbsp; 再次，添加语句 <code>and exists(select admin from admin)</code> 来猜解admin表中的列名admin;
##### &nbsp;&nbsp;&nbsp; 最后，添加语句 <code>and (select top 1 len (admin) from admin)>1</code> ，来猜解字段长度;
##### &nbsp;&nbsp;&nbsp; 添加<code>and (select top 1asc(mid(admin,1,1)) from admin)>97</code>来猜解字段中字符的ASCII码。通过以上四个步骤，反复猜解，即可得到数据库存储的用户名和密码。


<br />

## **实验步骤:**

#### **1.找到有注入漏洞的目标网站**

<br />

<p class="margin-left">
<b>●</b>目标站点: <code>http://192.168.1.3:8008</code> 选择链接 <code>http://192.168.1.3:8008/onews.asp?id=45</code>
</p>

<img src="/files/SQL injection principle - manually inject access database/1.png" widyh="400px" height="200px">

<br />

<p class="margin-left">
<b>○</b>测试链接，在链接末尾分别添加 <code>'</code> 、 <code>and 1=1</code> 和 <code>and 1=2</code>,网页显示分别如下
</p>

<img src="/files/SQL injection principle - manually inject access database/2.png" widyh="300px" height="150px">

<img src="/files/SQL injection principle - manually inject access database/3.png" widyh="300px" height="150px">

<img src="/files/SQL injection principle - manually inject access database/4.png" widyh="300px" height="150px">

<br />

<p class="margin-left">
<b>●</b>可见上述链接是有注入漏洞的
</p>

<br />

#### **2.猜解表名**

<br />

<p class="margin-left">
<b>●</b>在链接末尾添加 <code>and exists(select * from admin)</code> ,页面显示正常，说明存在表名[admin]
</p>

<img src="/files/SQL injection principle - manually inject access database/5.png" widyh="300px" height="150px">

<br />

#### **3.猜解列名**

<br />

<p class="margin-left">
<b>●</b>在链接末尾添加语句

<code>and exists(select admin from admin)</code> ,页面显示正常，即表中存在admin列
</p>

<br />

<p class="margin-left">
<b>○</b>在链接末尾添加语句

<code>and exists(select password from admin)</code> ,页面显示正常，即表中存在password列
</p>

<br />

#### **4.猜解字段内容**

<br />

<p class="margin-left">
<b>●</b>猜测字段的长度，在链接末尾输入语句

<code>and (select top 1 len(admin) from admin) > 1</code>,页面显示正常，数字依次加1，进行测试。若输入>5时显示数据库出错，则说明字段长度为5
</p>

<br />

<p class="margin-left">
<b>○</b>同样的方法，在链接末尾添加语句

<code>and (select top 1 asc(mid(admin,1,1)) from admin) > 97)</code> ,可猜解出第一条记录的第一位字符的ASCII码为97，对应a
</p>

<br />

<p class="margin-left">
<b>●</b>重复上述操作，可以得到admin、password的字段内容
</p>

<br />

## **实验总结:**

这次试验需要SQL基础，如果只是做完，很简单，但是因为去搞清给出的SQL语句什么含义，花了点时间去看了下SQL基础，了解了一下SQL语句;

同时也清楚了手工注入SQL语句的大概流程:

1.找出有注入漏洞的网页

2.猜解表名，看看是否有admin表

3.猜解列名，试试admin表中是否有admin和password这两列

4.猜解字段内容，一个个字符尝试猜出字段内容

为了提高手工注入猜解的效率，可以使用二分法逐渐缩小查询范围。






