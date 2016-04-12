---
id: 43
title: 用Privoxy转发socks代理，建http代理
date: 2016-02-19T21:38:36+08:00
author: Kanaan Austen
layout: post
guid: https://blog.nieyujiang.info/?p=43
permalink: /2016/02/19/using-privoxy-forwards-socks-proxy-build-http-proxy/
dsq_thread_id:
  - 4664233084
views:
  - 28
categories:
  - 黑科技
---
<!--wp-compress-html-->

<!--wp-compress-html no compression-->

有些软件不支持socks代理，只支持http代理。不像火狐那样都支持，于是有的时候要建http代理。

如果您有socks代理，想做一个http代理的话，这篇文章可能会有帮助。

**安装Privoxy**

&nbsp;

<pre class="prettyprint" ><code>&lt;br />brew install Privoxy

</code></pre>

**配置Privoxy**

配置文件默认是 `/usr/local/etc/privoxy/config(mac)` 或 `/etc/privoxy/config(linux)`
  
编辑它增加一行：

&nbsp;

<pre class="prettyprint" ><code>&lt;br />forward-socks5 / 127.0.0.1:1080 .

</code></pre>

&nbsp;

forward-socks5代表转发到socks5代理，/代表所有的URL都转发(也可以在这里写url patten)，127.0.0.1:1080是socks代理的位置，最后的一点.代表没有http代理，具体请上官网查阅。

保存即生效。

现在的127.0.0.1:8118就是一个http代理了。8118是privoxy默认的端口。

**开机自启**

&nbsp;

<pre class="prettyprint" ><code>&lt;br />ln -sfv /usr/local/opt/privoxy/*.plist ~/Library/LaunchAgents

</code></pre>

<!--wp-compress-html no compression-->

<!--wp-compress-html-->