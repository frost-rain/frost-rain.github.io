---
layout: post
title: 安装ruby -> jekyll
description: Win下安装ruby和jekyll的坑太多了，有必要记录下来，好好回想自己有多么的脑残
tag: jekyll
---

####引：<b style="color:Gold">win 对开发者及其不友好</b>，不能用命令行配置各种环境，而且在安装ruby时，总是会download失败；而安装jekyll时，也会时而报错。总之，win真的太辣鸡了。

安装ruby
---
<p align=right style="LightSlateGray;font-size:15">安ruby的Dev环境安了两次，首先是失败的方法</p>
###<b style="color:LightSkyBlue">1.分别下载ruby和Devkit的安装包。ruby如正常安装，Devkit则要命令行安装</b>



- #####解压Devkit至指定目录
 <div align=center> 
![](file:///F:/frost-rain.github.io/images/_posts/install ruby - jekyll/1.PNG)
 
 </div>

- #####安装Devkit

```
$ cd <install direction>   #进入安装目录
$ ruby dk.rb init          #初始化，我的config.yml已配置好了目录
$ ruby dk.rb install 	   #devkit安装
```


- #####安装jekyll

```
$ gem install jekyll   #download失败，卡住了
$ gem sources --add https://gems.ruby-china.com/ #换国内的gem源，提示SSL证书
$ gem sources --remove https://rubygems.org/

```

###### #  没有SSL证书，提示安装不正确，于是去找.gemrc文件修改配置忽略提示
###### #  但是.gemrc（主目录下）文件很久没找到，找到是很久后的事了
###### #  如下是添加的内容

```
---
:sources:
- https://gems.ruby-china.com
:ssl_verify_mode: 0
```

###<b style="color:LightSkyBlue">2.下载集成Devkit的包，直接安装</b>

- #####按提示安装，最后Devkit的安装会在命令行下，选 <b style="color:red">**[1]**</b></> enter 即可，没过一会便安好了，但是第一次的时候download失败（也许是和那边的服务器连接断了）

- #####ruby和Devkit都配置好了接下来就是jekyll

```
$ gem sources --add https://gems.ruby-china.com/ #换国内的gem源,无SSL证书问题
$ gem sources --remove https://rubygems.org/
$ gem install jekyll                            #此时依然报错，按照给出的未安装的gem包安装即可
```

- #####安装jekyll成功

```
$ cd  <username>.github.io    #进入博客所在文件夹，此处省略路径
$ jekyll server               #开启jekyll，会给出一个地址，复制访问就可以看博客了

```  
<br>


<div align=right style="font-size:20"> 至此，ruby及jekyll安装完毕 </div>

