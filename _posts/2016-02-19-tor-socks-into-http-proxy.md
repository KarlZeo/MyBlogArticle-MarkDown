---
id: 227
title: 将 Tor socks 转换成 http 代理
date: 2016-02-19T23:00:23+08:00
author: Kanaan Austen
layout: post
guid: https://blog.nieyujiang.info/?p=227
permalink: /2016/02/19/tor-socks-into-http-proxy/
dsq_thread_id:
  - 4688431385
views:
  - 20
categories:
  - 黑科技
---
<!--wp-compress-html-->

<!--wp-compress-html no compression-->

你可以通过不同的 Tor 工具来使用 Tor 服务，如 Tor 浏览器、Foxyproxy 和其它东西，像 wget 和 aria2 这样的下载管理器不能直接使用 Tor socks 开始匿名下载，因此我们需要一些工具来将 Tor socks 转换成 http 代理，这样就能用它来下载了。

**注意**：本教程基于 Debian ，其他发行版会有些不同，因此如果你的发行版是基于 Debian 的，就可以直接使用下面的配置了。

### Polipo

这个服务会使用 8123 端口和 127.0.0.1 的 IP 地址，使用下面的命令来在计算机上安装 Polipo：

<pre class="prettyprint" ><code>apt install polipo
</code></pre>

现在使用如下命令打开 Polipo 的配置文件：

<pre class="prettyprint" ><code>sudo nano /etc/polipo/config
</code></pre>

在文件最后加入下面的行：

<pre class="prettyprint" ><code>proxyAddress = "::0"
allowedClients = 192.168.1.0/24
socksParentProxy = "localhost:9050"
socksProxyType = socks5
</code></pre>

用如下的命令来重启 Polipo：

<pre class="prettyprint" ><code>sudo service polipo restart
</code></pre>

现在 Polipo 已经安装好了！在匿名的世界里做你想做的吧！下面是使用的例子：

<pre class="prettyprint" ><code>pdmt -l "link" -i 127.0.01 -p 8123
</code></pre>

通过上面的命令 PDMT（Persian 下载器终端）会匿名地下载你的文件。

### Proxychains

在此服务中你可以设置使用 Tor 或者 Lantern 代理，但是在使用上它和 Polipo 和 Privoxy 有点不同，它不需要使用任何端口！使用下面的命令来安装：

<pre class="prettyprint" ><code>sudo apt install proxychains
</code></pre>

用这条命令来打开配置文件：

<pre class="prettyprint" ><code>sudo nano /etc/proxychains.conf
</code></pre>

现在添加下面的代码到文件底部，这里是 Tor 的端口和 IP：

<pre class="prettyprint" ><code>socks5 127.0.0.1 9050
</code></pre>

如果你在命令的前面加上“proxychains”并运行，它就能通过 Tor 代理来运行：

<pre class="prettyprint" ><code>proxychains firefoxt
proxychains aria2c
proxychains wget
</code></pre>

### Privoxy

Privoxy 使用 8118 端口，可以很轻松地通过 privoxy 包来安装：

<pre class="prettyprint" ><code>sudo apt install privoxy
</code></pre>

我们现在要修改配置文件：

<pre class="prettyprint" ><code>sudo nano /etc/pivoxy/config
</code></pre>

在文件底部加入下面的行：

<pre class="prettyprint" ><code>forward-socks5 / 127.0.0.1:9050 .
forward-socks4a / 127.0.0.1:9050 .
forward-socks5t / 127.0.0.1:9050 .
forward 192.168.*.*/ .
forward 10.*.*.*/ .
forward 127.*.*.*/ .
forward localhost/ .
</code></pre>

重启服务：

<pre class="prettyprint" ><code>sudo service privoxy restart
</code></pre>

服务已经好了！端口是 8118，IP 是 127.0.0.1，就尽情使用吧！

<!--wp-compress-html no compression-->

<!--wp-compress-html-->