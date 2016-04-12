---
id: 251
title: 流量加速插件 FinalSpeed介绍及一键安装教程
date: 2016-02-19T23:05:13+08:00
author: Kanaan Austen
layout: post
guid: https://blog.nieyujiang.info/?p=251
permalink: /2016/02/19/flow-accelerated-introduction-of-plug-finalspeed-and-one-click-installation-tutorial/
flavour_num_words:
  - 333
dsq_thread_id:
  - 4624272838
views:
  - 14
categories:
  - Linux
---
<!--wp-compress-html-->

<!--wp-compress-html no compression-->

### 一.介绍

官方介绍：FinalSpeed是高速双边加速软件,可加速所有基于tcp协议的网络服务,在高丢包和高延迟环境下,仍可达到90%的物理带宽利用率,即使高峰时段也能轻松跑满带宽.

用途：可以压缩流量发包（双边），与Net-Speed多发包不同的是，FinalSpeed是压缩流量以增加传输成功率，这样就不会多耗费VPS流量，但是有可能对同机房的网络稳定造成影响。

### 二.适用范围

1、客户端：Windows、OS X（需要java）

2、服务端：在装有SS的Windows服务器或者Linux服务器（Debian/CentOS/Ubuntu）

3、服务端架构要求：Openvz、Xen等，适用于绝大部分VPS，包括Banwagong等廉价VPS

### 三.服务端部署

1、Windows服务端：

下载：[点我](http://www.abclite.cn/redirect/aHR0cDovL2ZzLmQxc20ubmV0L2ZpbmFsc3BlZWQvZmluYWxzcGVlZF9zZXJ2ZXJfd2luZG93czEuMC56aXA=)

2、Linux（Debian/CentOS/Ubuntu）服务端一键安装：

<pre class="prettyprint" ><code>wget http://fs.d1sm.net/finalspeed/install_fs.sh
chmod +x install_fs.sh
./install_fs.sh 2&gt;&1 | tee install.log
</code></pre>

安装完成后会提示如下表示已经成功运行：
  
![](http://cdn.abclite.cn/wp-content/uploads/2016/01/FS1.jpg "流量加速插件 FinalSpeed介绍及一键安装教程")
  
A、相关命令行：

<pre class="prettyprint" ><code>安装完成后可通过查看日志看是否运行：tail -f /fs/server.log
卸载：sh /fs/stop.sh ; rm -rf /fs
停止：sh /fs/stop.sh
重新启动：sh /fs/restart.sh; tail -f /fs/server.log
</code></pre>

B、设置服务端口：

<pre class="prettyprint" ><code>默认udp 150和tcp 150 ,由于finalspeed的工作原理,请不要在本机防火墙开放finalspeed所使用的tcp端口.
linux版：mkdir -p /fs/cnf/ ; echo 端口号 &gt; /fs/cnf/listen_port ; sh /fs/restart.sh
windows版：在cnf目录下新建文件listen_port,文件内容为端口号.
</code></pre>

C、设置开机启动：

<pre class="prettyprint" ><code>chmod +x /etc/rc.local
vi /etc/rc.local
加入
sh /fs/start.sh
</code></pre>

D、每天晚上3点自动重启：

<pre class="prettyprint" ><code>crontab -e
加入
0 3 * * * sh /fs/restart.sh
</code></pre>

E、还要注意，已经在运行了没有停止情况下重复启动是会报错的，所以最好先停止或者重启。
  
###四,客户端部署
  
Windows客户端下载：[点我](http://www.abclite.cn/redirect/aHR0cDovL2ZzLmQxc20ubmV0L2ZpbmFsc3BlZWQvZmluYWxzcGVlZF9pbnN0YWxsMS4wLmV4ZQ==)

OS X/Linux客户端下载：[点我](http://www.abclite.cn/redirect/aHR0cDovL2ZzLmQxc20ubmV0L2ZpbmFsc3BlZWQvZmluYWxzcGVlZF9jbGllbnQxLjAuemlw) （需安装Java套件）

<pre class="prettyprint" ><code>注意问题
1.服务器必须同时部署FinalSpeed服务端才能进行加速.
2.客户端必须准确设置物理带宽,最终加速的速度不会超过所设置的带宽值,如果设置值高于实际带宽会造成丢包,导致速度变慢.
3.客户端首选tcp协议,如果udp不稳定,请切换到tcp.
4.若服务器为openvz架构,客户端只能选择udp协议,其他架构同时支持tcp和udp协议.
5.windows客户端使用tcp协议时不兼容锐速,停止锐速后可以正常运行.
6.FinalSpeed不提供加密功能,如有安全需求,不要直接加速明文协议.
</code></pre>

假设服务器IP为10.10.10.10,finalspeed端口为默认150,ss端口为8989，加速前提ss服务端运行正常,ss客户端也能正常登录。

1.运行FinalSpeed客户端,填写服务器地址 10.10.10.10 .

![](http://cdn.abclite.cn/wp-content/uploads/2016/01/FS2.jpg "流量加速插件 FinalSpeed介绍及一键安装教程")
  
2.点击添加,增加加速端口,加速端口为ss端口8989,如果为其他端口,请相应修改,本地端口任意,这里是2000 .

![](http://cdn.abclite.cn/wp-content/uploads/2016/01/FS3.jpg "流量加速插件 FinalSpeed介绍及一键安装教程")
  
3.打开ss客户端,添加服务器,服务器IP为127.0.0.1,服务器端口为加速端口对应的本地端口,这里是2000,然后设置你的ss密码,加密方式.

![](http://cdn.abclite.cn/wp-content/uploads/2016/01/FS4.jpg "流量加速插件 FinalSpeed介绍及一键安装教程")

4.确定保存,选择使用刚添加的服务器,并设置浏览器代理,成功连接后,FinalSpeed状态栏会出现&#8221;连接服务器成功&#8221;提示.

<pre class="prettyprint" ><code>通过实际使用，在openVZ服务器还是有一定速度提升，在Xen下还能和锐速相互使用，不过提升不明显，该插件的出现还是帮助了一大帮搬瓦工使用者用SS，不过无论什么插件还是没有锐速来的实在，有能力还是记得买Xen架构的VPS。
该插件不能和SSR共同使用。
</code></pre>

<!--wp-compress-html no compression-->

<!--wp-compress-html-->