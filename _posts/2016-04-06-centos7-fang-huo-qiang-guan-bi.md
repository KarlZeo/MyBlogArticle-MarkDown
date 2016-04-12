---
id: 379
title: CentOS7 防火墙
date: 2016-04-06T17:44:04+08:00
author: Kanaan Austen
layout: post
guid: https://blog.nieyujiang.info/?p=379
permalink: /2016/04/06/centos7-fang-huo-qiang-guan-bi/
views:
  - 10
dsq_thread_id:
  - 4727238854
categories:
  - Linux
---
<!--wp-compress-html-->

<!--wp-compress-html no compression-->

CentOS 7 的防火墙由之前版本的 `iptables` 换成了 `firewall`

## 1. 关闭防火墙 {#toc_0}

<pre class="prettyprint" ><code>systemctl stop firewalld.service
</code></pre>

## 2. 关闭开机启动 {#toc_1}

<pre class="prettyprint" ><code>systemctl disable firewalld.service
</code></pre>

## 3. 安装iptables防火墙 {#toc_2}

<pre class="prettyprint" ><code>yum install iptables-services
</code></pre>

## 4. 配置iptables防火墙，打开指定端口 {#toc_3}

略

## 5. 设置iptables防火墙开机启动 {#toc_4}

<pre class="prettyprint" ><code>systemctl enable iptables
</code></pre>

<!--wp-compress-html no compression-->

<!--wp-compress-html-->