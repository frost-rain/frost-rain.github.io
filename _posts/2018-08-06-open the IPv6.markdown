---
layout: post
title: "开启IPv6"
description: "开启IPv6"
tag: [XX-Net,IPv6]
---

<style>
#padding{
padding-left:68px
}
#td{
font-size:1.2em;
}
#codemargin{
margin:20px;
}
</style>

<br />

**概述**
---
---

#### 开启IPv6，有以下几种方法

1.&nbsp; 开通IPv6 原生支持，如果是自家的网可以联系运营商开启

2.&nbsp; 高校教育网一般开通了原生IPv6，但是我们学校并没有，若是教育网，可以通过教育网 ISATAP 隧道开启，但是，学校的网依然不支持

3.&nbsp; 通过 teredo 隧道获取IPv6支持，本文以此方法开启IPv6

<br />

**Windows**
---
---

<p  style="color:firebrick">注意,找到 网络和共享中心 - 更改适配器设置 - 本地连接（无线网络则找到WLAN或蓝牙网络连接）- 属性，把 IPv6协议 前面的勾去掉，确定。否则会出现一些奇怪的问题</p>

<br />

1.&nbsp; 打开cmd或powershell，输入以下命令

```cmd
  // 设置 Teredo 服务器，默认为：win10.ipv6.microsoft.com
  // 建议将default改为win10.ipv6.microsoft.com
  netsh interface teredo set state enterpriseclient server=default
  
  // 测试 IPv6 连接
  ping -6 ipv6.test-ipv6.com
  ping -6 [2001:470:1:18::125]

  // 重置 IPv6 配置
  netsh interface ipv6 reset
```
<p id="padding"> 
<b>●</b> 重启系统
</p>

<p id="padding"> 
<b>○</b> 通过命令 <code>ipconfig /all</code> 查看当前网络信息，看到 <code>Teredo Tunneling Pseudo-Interface</code> 有以 2001 开头的IPv6地址即可
</p>	

2.&nbsp; 若上述方法不行，则可以尝试一下两种方法

```cmd
  // 第一种：修改 Teredo 服务器为 teredo.remlab.net
  netsh interface teredo set state server=teredo.remlab.net

  // 第二种：先卸载当前 Teredo 适配器再重新启用
  netsh interface Teredo set state disable
  netsh interface Teredo set state type=default
  ping -6 ipv6.test-ipv6.com
``` 

<br />

**Linux**
---
---

<p style="color:firebrick">这里以Ubuntu为例</p>

<br />

1.&nbsp; 安装虚拟网卡miredo

<code id="codemargin">sudo apt-get install miredo</code>

2.&nbsp; 查看网卡配置

<code id="codemargin" >sudo apt-get install net-tools</code> 

<code id="codemargin">ifconfig</code>

&nbsp;&nbsp;&nbsp; 在结果中可以看见一个叫 teredo 的虚拟网卡

3.&nbsp; 启动miredo（重启后有可能需要手动启动）

<code id="codemargin">sudo miredo</code>

