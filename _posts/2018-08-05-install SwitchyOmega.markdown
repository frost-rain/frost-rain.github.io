---
layout: post
title: "配置 SwitchyOmega"
description: "安装及配置 SwitchyOmega"
tag: [XX-Net,SwitchyOmega]
---

<style>
#padding{
padding-left:68px
}

#table{
border: 2px solid white ;
padding: 2px solid white;
}
</style>

<br />

**概述**
---
---

#### 使用SwitchyOmega切换代理非常方便。对于未被墙的网站，有时候网页加载速度过慢，下载文件的速度也很感人，这时候可以利用SwitchyOmega将此网站加入代理中，加快网站资源加载速度。

**步骤**
---
---


1.&nbsp; 安装SwitchyOmega

<p id="padding"> 
<b>●</b> 将SwitchyOmega.crx拖入浏览器的extensions(扩展程序)界面
</p>

<br />

<img src="/files/install SwitchyOmega/1.PNG" />

<p id="padding">
<b>○</b> 点击跳过教程
</p>

2.&nbsp; 导入OmegaOptions.bak加载情景模式

<p id="padding">
<b>●</b> 进入设置界面，跳过教程，导入OmegaOptions.bak
</p>

<br />

<img src="/files/install SwitchyOmega/2.jpg" width="700" height="400" />

<img src="/files/install SwitchyOmega/3.jpg" width="700" height="400" />

<p id="padding"> 
<b>○</b> 点击情景模式中的 GAE-Proxy自动切换 ,跳过教程
</p>

<br />

<img src="/files/install SwitchyOmega/4.jpg" width="700" height="400" />

<p id="padding">
<b>●</b> 下拉点击“立即更新情景模式” 
</p>

<br />

<img src="/files/install SwitchyOmega/5.png" width="700" height="400" />

3.&nbsp; 调整

<p id="padding"> 
<b>●</b> 右上角点击SwitchyOmega，切换成“GAE-Proxy自动切换”，如果使用的是X-Tunnel或SS，则点击“X-Tunnel自动切换”(X-Tunnel需付费，不考虑)。 
</p>

<br />

<img src="/files/install SwitchyOmega/6.jpg" width="250" height="300" />

<p id="padding">
<b>○</b> 最后，将右下角任务栏内的XX-Net切换为“取消全局代理”
</p>

<br />

<img src="/files/install SwitchyOmega/7.jpg" width="200" height="260" />

4.&nbsp; CA证书的导入

<p id="padding"> 
<b>●</b> 正常情况下，证书都是自动导入的。非正常情况下需要手动导入证书，比如遇到“您打开的链接不是私密连接”。这时候，点击浏览器的高级设置，再点击管理证书手动导入证书
</p>

<br />

<img src="/files/install SwitchyOmega/8.png" width="500" height="300" />

<p id="padding">
<b>○</b> 导入证书

<br />

<table id="table"> <tr>
<th> <img src="/files/install SwitchyOmega/9.png" width="330" height="270" /> </th>
<th> <img src="/files/install SwitchyOmega/10.png" width="330" height="270" /> </th>
</tr> </table>

<table id="table"> <tr>
<th> <img  src="/files/install SwitchyOmega/11.png" width="300" height="250" /> </th>
<th> <img src="/files/install SwitchyOmega/12.png"  width="300" height="250" /> </th>
</tr></table>

<table id="table"> <tr>
<th> <img src="/files/install SwitchyOmega/13.png" width="300" height="250" /> </th>
<th> <img src="/files/install SwitchyOmega/14.png" width="300" height="250" /> </th>
</tr></table>

4.&nbsp; SwitchyOmega安装配置完成