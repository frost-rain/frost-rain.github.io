---
layout: post
title: "利用 XX-Net 翻墙"
description: "利用 XX-Net 翻墙"
tag: XX-Net
---

<style>
#padding{
padding-left:68px
}
#td{
font-size:1.2em;
}
attention{
padding:70px;
}
#codemargin{
margin:20px;
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

XX-Net 包含两个模块:

<table >
<tr>
	<th id="td">模块</th>
	<th id="td">GAE_proxy</th>
	<th id="td">X-Tunnel</th>
</tr>
<tr>
	<td id="td">联通性</td>
	<td id="td">依赖IPv6</td>
	<td id="td">更多通道</td>
</tr>
<tr>
	<td id="td">速度</td>
	<td id="td">流畅</td>
	<td id="td">下载快速，稍微延迟</td>
</tr>
<tr>
	<td id="td">安全性</td>
	<td id="td">Google可看到通信内容</td>
	<td id="td">支持完整https加密</td>
</tr>
<tr>
	<td id="td">易用</td>
	<td id="td">需开启Ipv6，部署服务端，导入证书</td>
	<td id="td">简单</td>
</tr>
<tr>
	<td id="td">兼容性</td>
	<td id="td">部分网站不支持</td>
	<td id="td">无问题</td>
</tr>
<tr>
	<td id="td">收费</td>
	<td id="td">免费</td>
	<td id="td">付费</td>
</tr>
</table>



#### 要科学上网，需要进行以下步骤:

1.&nbsp; 获取XX-Net

<p id="padding"> 
<b>●</b> XX-Net Github 项目地址:&nbsp;&nbsp;
<a href="https://github.com/XX-net/XX-Net" target="blank">  点我 ~ o(*￣▽￣*)ブ  </a>
</p>

<p id="padding"> 
<b>○</b> 由于 Github上下载速度过慢，所以这里给出 XX-Net 的下载链接: 
<a href="/files/XX-Net config/XX-Net.zip"> XX-Net 下载</a>
</p>

<p id="padding">
<b>●</b> 也可以直接clone repository,但是Github上这个项目的clone也无比的慢，可以利用码云导入项目后再clone，速度较快
</p>

2.&nbsp; 安装并初始化

3.&nbsp; 设置代理

4.&nbsp; 装浏览器插件，利用插件进行自动代理

<br />

**Windows**
---
---

1.&nbsp; 以管理员身份运行start.bat

&nbsp;&nbsp;&nbsp; 会弹出安装CA证书的界面，同意即可
   
2.&nbsp; 安装完毕后会自动启动，并弹出浏览器，访问<a href=" http://localhost:8085/" target="blank">配置界面</a>

3.&nbsp; 左键单击右下角的图标可进入配置界面，右键单击显示常用功能菜单，根据自己的需要调整功能

&nbsp;&nbsp;&nbsp; ps: 有SwitchyOmega的话选择“取消全局代理”

4.&nbsp; 由于GAEProxy与X-Tunnel只有GAEProxy是免费的，而GAEProxy又依赖于IPv6，一般情况下，大多数用户只能在IPv4网络上访问网站，所以我们需要通过某些隧道开启IPv6&nbsp;&nbsp;
<a href="/2018/08/open-the-IPv6/" target="blank">(╯● ∇ ●)╯方法丢给你</a>


5.&nbsp; 浏览器使用代理切换插件SwitchyOmega&nbsp;&nbsp; 
<a href="/2018/08/install-SwitchyOmega/" target="blank">＜( ￣︿￣)︵安︵装︵方︵法</a>

<br />

**Linux**
---
---

<p style="color:firebrick">这里以Ubuntu为例</p>

<br />

1.&nbsp; 先开启IPv6&nbsp;&nbsp;
<a href="/2018/08/open-the-IPv6/" target="blank">(╯● ∇ ●)╯方法丢给你</a>

2.&nbsp; 安装一些可能用的得到的组件

```bash
sudo apt-get install python-openssl
sudo apt-get install libffi-dev
sudo apt-get install python-gtk2
sudo apt-get install python-appindicator
sudo apt-get install libnss3-tools
```

3.&nbsp; 手动配置HTTP代理localhost 8087，地址栏输入127.0.0.1:8087

<br />

<table id="table"><tr>
<th><img src="/files/XX-Net config/1.jpg" width="400" height="250" /> </th>
<th> <img src="/files/XX-Net config/2.jpg" width="300" height="250" /> </th>
</tr></table>

4.&nbsp; 通过终端进入XX-Net所在文件夹，运行start文件，开启浏览器即可访问谷歌

<code id="codemargin">cd /../XX-Net</code>

<code id="codemargin">./start</code>

5.&nbsp; 后台运行：在终端中运行:

<code id="codemargin">xx_net.sh start/stop/restart</code>

&nbsp;&nbsp;&nbsp; 开机自启：在/etc/rc.local中添加一行:

<code id="codemargin">sudo /home/username/xxnet/xx_net.sh start</code>

6.&nbsp; 安装SwitchyOmega，linux下与win10有些许不同（也许只是我）

<p id="padding"> 
<b>●</b> 此时已经翻墙成功，但为了方便，装SwitchyOmega为好
</p>

<p id="padding">
<b>○</b> XX-Net内的SwitchyOmega及证书都装不了，前者需要证书，而CA.crt偏偏装不了
</p>

<p id="padding"> 
<b>●</b> 因为已经翻墙，所以直接打开Chrome的扩展程序，进入谷歌商店直接搜SwitchyOmega安装即可
</p>

<p id="padding">
<b>○</b> 配置SwitchyOmega如后&nbsp;&nbsp;
<a href="/2018/08/install-SwitchyOmega/" target="blank">o(๑◕ ▽ ◕3)ブ~~拿走不谢</a>
</p>

7.&nbsp; 浪吧（就是想加最后一行）