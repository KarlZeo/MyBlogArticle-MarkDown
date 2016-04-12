---
id: 46
title: 使用 HAProxy 来中转国外代理
date: 2016-02-19T21:39:25+08:00
author: Kanaan Austen
layout: post
guid: https://blog.nieyujiang.info/?p=46
permalink: /2016/02/19/transit-foreign-agents-using-haproxy/
dsq_thread_id:
  - 4657961109
views:
  - 9
categories:
  - 黑科技
---
HAProxy是一款免费、快速并且可靠的一种代理解决方案，支持高可用性、负载均衡特性，同时适用于做基于TCP和HTTP的应用的代理。对于一些负载较大的Web站点，使用HAProxy特别合适。HAProxy能够支撑数以万计的并发连接。它的配置简单，能够很容易整合大我们现有的应用架构之中。

所以，用来中转国内代理真是最好不过了。。。。
  
**安装**

`wget http://www.haproxy.org/download/1.5/src/haproxy-1.5.14.tar.gz`
  
`tar xvzf haproxy-1.5.14.tar.gz`
  
`cd haproxy-1.5.14`
  
`make TARGET=linux26`
  
`make install`
  
默认安装，HAProxy对应的配置文件的存放路径为/etc/haproxy/haproxy.cfg。
  
如果你想熟练使用 HAProxy 请自行谷歌。
  
如果你只想中转国外代理，均衡负载代理，请看下面：

`global`
  
`ulimit-n 51200`

`defaults`
  
`log global`
  
`mode tcp`
  
`option dontlognull`
  
`timeout connect 1000`
  
`timeout client 150000`
  
`timeout server 150000`
  
`#设定中转服务器的ss端口 客户端连接请使用大陆vps的ip 连接端口这里重新自定为10800`
  
`frontend ss-in`
  
`bind *:10800`
  
`default_backend ss-out`
  
`#部署了ss的美国vps的ip以及端口 这里举例9999`
  
`backend ss-out`
  
`server server1 US_VPS_IP:9999 maxconn 20480`
  
`#设定中转服务器的ocserv端口 客户端连接请使用大陆vps的ip 连接端口这里重新自定为4430`
  
`frontend oc-in`
  
`bind *:4430`
  
`default_backend oc-out`
  
`#部署了openconnect的美国vps的ip以及tcp端口 这里举例999`
  
`backend oc-out`
  
`server server1 US_VPS_IP:999 maxconn 20480`
  
由于是中转，证书会出现不符的现象，在客户端使用anyconnect时候，需要关掉客户端设置中的“阻止不信任的服务器”。

我们对上面配置文件的内容，适当的扩展，做简单的解释：

global段
  
global段用于配置进程级的参数。官网文档基于参数的功能，将global配置参数分为3组：

进程管理和安全
  
性能调优
  
调试
  
具体内容可以参考文档详细介绍。

defaults段
  
defaults段主要是代理配置的默认配置段，设置默认参数，这些默认的配置可以在后面配置的其他段中使用。如果其他段中想修改默认的配置参数，只需要覆盖defaults段中的出现配置项内容。
  
关于defaults段可以配置的参数，可以参考官网文档的详细介绍。

frontend段
  
frontend段主要配置前端监听的Socket相关的属性，也就是接收请求链接的虚拟节点。这里除了配置这些静态的属性，还可以根据一定的规则，将请求重定向到配置的backend上，backend可能配置的是一个服务器，也可能是一组服务器（集群）。

backend段
  
backend段主要是配置的实际服务器的信息，通过frontend配置的重定向请求，转发到backend配置的服务器上。

**启动HAProxy代理**

启动非常简单，执行如下命令即可：sudo haproxy -f /etc/haproxy/haproxy.cfg