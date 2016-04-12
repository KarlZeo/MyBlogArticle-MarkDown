---
id: 267
title: '使用 netcat [nc] 命令对 Linux 和 Unix 进行端口扫描'
date: 2016-02-19T23:11:03+08:00
author: Kanaan Austen
layout: post
guid: https://blog.nieyujiang.info/?p=267
permalink: /2016/02/19/using-netcat-nc-port-scan-commands-for-linux-and-unix/
dsq_thread_id:
  - 4593469704
flavour_num_words:
  - 665
views:
  - 5
categories:
  - Linux
---
我如何在自己的服务器上找出哪些端口是开放的？如何使用 nc 命令进行端口扫描来替换 [Linux 或类 Unix 中的 nmap 命令](https://linux.cn/article-2561-1.html)？

nmap (“Network Mapper”)是一个用于网络探测和安全审核的开源工具。如果 nmap 没有安装或者你不希望使用 nmap，那你可以用 netcat/nc 命令进行端口扫描。它对于查看目标计算机上哪些端口是开放的或者运行着服务是非常有用的。你也可以使用 [nmap 命令进行端口扫描](https://linux.cn/article-2561-1.html) 。

<p class="article_img">
  <img src="https://blog.nieyujiang.info/wp-content/uploads/2016/02/bfad6a5661c7d72ef46468356bd52d0f.gif" alt="使用 netcat [nc] 命令对 Linux 和 Unix 进行端口扫描" title="使用 netcat [nc] 命令对 Linux 和 Unix 进行端口扫描" alt="" />
</p>

### 如何使用 nc 来扫描 Linux，UNIX 和 Windows 服务器的端口呢？ {#toc_1}

如果未安装 nmap，试试 nc/netcat 命令，如下所示。-z 参数用来告诉 nc 报告开放的端口，而不是启动连接。在 nc 命令中使用 -z 参数时，你需要在主机名/ip 后面限定端口的范围和加速其运行：

<ol class="linenums">
  <li class="L0">
    <code>&lt;span class="com">### 语法 ###&lt;/span></code>
  </li>
  <li class="L1">
    <code>&lt;span class="com">### nc -z -v {host-name-here} {port-range-here}&lt;/span></code>
  </li>
  <li class="L2">
    <code>&lt;span class="pln">nc &lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="pln">z &lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="pln">v host&lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="pln">name&lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="pln">here &lt;/span>&lt;span class="kwd">ssh&lt;/span></code>
  </li>
  <li class="L3">
    <code>&lt;span class="pln">nc &lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="pln">z &lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="pln">v host&lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="pln">name&lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="pln">here &lt;/span>&lt;span class="lit">22&lt;/span></code>
  </li>
  <li class="L4">
    <code>&lt;span class="pln">nc &lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="kwd">w&lt;/span> &lt;span class="lit">1&lt;/span> &lt;span class="pun">-&lt;/span>&lt;span class="pln">z &lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="pln">v server&lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="pln">name&lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="pln">here port&lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="typ">Number&lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="pln">her&lt;/span></code>
  </li>
  <li class="L5">
    <code></code>
  </li>
  <li class="L6">
    <code>&lt;span class="com">### 扫描 1 to 1023 端口 ###&lt;/span></code>
  </li>
  <li class="L7">
    <code>&lt;span class="pln">nc &lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="pln">zv vip&lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="lit">1.vsnl&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="pln">nixcraft&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="kwd">in&lt;/span> &lt;span class="lit">1&lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="lit">1023&lt;/span></code>
  </li>
</ol>

输出示例:

<ol class="linenums">
  <li class="L0">
    <code>&lt;span class="typ">Connection&lt;/span>&lt;span class="pln"> to localhost &lt;/span>&lt;span class="lit">25&lt;/span>&lt;span class="pln"> port &lt;/span>&lt;span class="pun">[&lt;/span>&lt;span class="pln">tcp&lt;/span>&lt;span class="pun">/&lt;/span>&lt;span class="pln">smtp&lt;/span>&lt;span class="pun">]&lt;/span>&lt;span class="pln"> succeeded&lt;/span>&lt;span class="pun">!&lt;/span></code>
  </li>
  <li class="L1">
    <code>&lt;span class="typ">Connection&lt;/span>&lt;span class="pln"> to vip&lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="lit">1.vsnl&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="pln">nixcraft&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="kwd">in&lt;/span> &lt;span class="lit">25&lt;/span>&lt;span class="pln"> port &lt;/span>&lt;span class="pun">[&lt;/span>&lt;span class="pln">tcp&lt;/span>&lt;span class="pun">/&lt;/span>&lt;span class="pln">smtp&lt;/span>&lt;span class="pun">]&lt;/span>&lt;span class="pln"> succeeded&lt;/span>&lt;span class="pun">!&lt;/span></code>
  </li>
  <li class="L2">
    <code>&lt;span class="typ">Connection&lt;/span>&lt;span class="pln"> to vip&lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="lit">1.vsnl&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="pln">nixcraft&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="kwd">in&lt;/span> &lt;span class="lit">80&lt;/span>&lt;span class="pln"> port &lt;/span>&lt;span class="pun">[&lt;/span>&lt;span class="pln">tcp&lt;/span>&lt;span class="pun">/&lt;/span>&lt;span class="pln">http&lt;/span>&lt;span class="pun">]&lt;/span>&lt;span class="pln"> succeeded&lt;/span>&lt;span class="pun">!&lt;/span></code>
  </li>
  <li class="L3">
    <code>&lt;span class="typ">Connection&lt;/span>&lt;span class="pln"> to vip&lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="lit">1.vsnl&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="pln">nixcraft&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="kwd">in&lt;/span> &lt;span class="lit">143&lt;/span>&lt;span class="pln"> port &lt;/span>&lt;span class="pun">[&lt;/span>&lt;span class="pln">tcp&lt;/span>&lt;span class="pun">/&lt;/span>&lt;span class="pln">imap&lt;/span>&lt;span class="pun">]&lt;/span>&lt;span class="pln"> succeeded&lt;/span>&lt;span class="pun">!&lt;/span></code>
  </li>
  <li class="L4">
    <code>&lt;span class="typ">Connection&lt;/span>&lt;span class="pln"> to vip&lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="lit">1.vsnl&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="pln">nixcraft&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="kwd">in&lt;/span> &lt;span class="lit">199&lt;/span>&lt;span class="pln"> port &lt;/span>&lt;span class="pun">[&lt;/span>&lt;span class="pln">tcp&lt;/span>&lt;span class="pun">/&lt;/span>&lt;span class="pln">smux&lt;/span>&lt;span class="pun">]&lt;/span>&lt;span class="pln"> succeeded&lt;/span>&lt;span class="pun">!&lt;/span></code>
  </li>
  <li class="L5">
    <code>&lt;span class="typ">Connection&lt;/span>&lt;span class="pln"> to vip&lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="lit">1.vsnl&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="pln">nixcraft&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="kwd">in&lt;/span> &lt;span class="lit">783&lt;/span>&lt;span class="pln"> port &lt;/span>&lt;span class="pun">[&lt;/span>&lt;span class="pln">tcp&lt;/span>&lt;span class="com">/*] succeeded!&lt;/span></code>
  </li>
  <li class="L6">
    <code>&lt;span class="com">Connection to vip-1.vsnl.nixcraft.in 904 port [tcp/vmware-authd] succeeded!&lt;/span></code>
  </li>
  <li class="L7">
    <code>&lt;span class="com">Connection to vip-1.vsnl.nixcraft.in 993 port [tcp/imaps] succeeded!&lt;/span></code>
  </li>
</ol>

你也可以扫描单个端口:

<ol class="linenums">
  <li class="L0">
    <code>&lt;span class="pln">nc &lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="pln">zv v&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="pln">txvip1 &lt;/span>&lt;span class="lit">443&lt;/span></code>
  </li>
  <li class="L1">
    <code>&lt;span class="pln">nc &lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="pln">zv v&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="pln">txvip1 &lt;/span>&lt;span class="lit">80&lt;/span></code>
  </li>
  <li class="L2">
    <code>&lt;span class="pln">nc &lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="pln">zv v&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="pln">txvip1 &lt;/span>&lt;span class="lit">22&lt;/span></code>
  </li>
  <li class="L3">
    <code>&lt;span class="pln">nc &lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="pln">zv v&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="pln">txvip1 &lt;/span>&lt;span class="lit">21&lt;/span></code>
  </li>
  <li class="L4">
    <code>&lt;span class="pln">nc &lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="pln">zv v&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="pln">txvip1 smtp&lt;/span></code>
  </li>
  <li class="L5">
    <code>&lt;span class="pln">nc &lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="pln">zvn v&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="pln">txvip1 ftp&lt;/span></code>
  </li>
  <li class="L6">
    <code></code>
  </li>
  <li class="L7">
    <code>&lt;span class="com">### 使用1秒的超时值来更快的扫描 ###&lt;/span></code>
  </li>
  <li class="L8">
    <code>&lt;span class="pln">netcat &lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="pln">v &lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="pln">z &lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="pln">n &lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="kwd">w&lt;/span> &lt;span class="lit">1&lt;/span>&lt;span class="pln"> v&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="pln">txvip1 &lt;/span>&lt;span class="lit">1&lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="lit">1023&lt;/span></code>
  </li>
</ol>

输出示例:

<p class="article_img">
  <img title="图01：Linux/Unix：使用 Netcat 来测试 TCP 和 UDP 与服务器建立连接" src="https://blog.nieyujiang.info/wp-content/uploads/2016/02/07a768045ba2dca4447d38efb3a191e6.jpg" alt="使用 netcat [nc] 命令对 Linux 和 Unix 进行端口扫描" title="使用 netcat [nc] 命令对 Linux 和 Unix 进行端口扫描" alt="图01：Linux/Unix：使用 Netcat 来测试 TCP 和 UDP 与服务器建立连接" />
</p>

<p class="article_img_desc">
  <em>图01：Linux/Unix：使用 Netcat 来测试 TCP 和 UDP 与服务器建立连接</em>
</p>

  1. -z : 端口扫描模式即零 I/O 模式。
  2. -v : 显示详细信息 [使用 -vv 来输出更详细的信息]。
  3. -n : 使用纯数字 IP 地址，即不用 DNS 来解析 IP 地址。
  4. -w 1 : 设置超时值设置为1。

更多例子:

<ol class="linenums">
  <li class="L0">
    <code>&lt;span class="pln">$ netcat &lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="pln">z &lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="pln">vv www&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="pln">cyberciti&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="pln">biz http&lt;/span></code>
  </li>
  <li class="L1">
    <code>&lt;span class="pln">www&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="pln">cyberciti&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="pln">biz &lt;/span>&lt;span class="pun">[&lt;/span>&lt;span class="lit">75.126&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="lit">153.206&lt;/span>&lt;span class="pun">]&lt;/span> &lt;span class="lit">80&lt;/span> &lt;span class="pun">(&lt;/span>&lt;span class="pln">http&lt;/span>&lt;span class="pun">)&lt;/span>&lt;span class="pln"> open&lt;/span></code>
  </li>
  <li class="L2">
    <code>&lt;span class="pln"> sent &lt;/span>&lt;span class="lit">0&lt;/span>&lt;span class="pun">,&lt;/span>&lt;span class="pln"> rcvd &lt;/span>&lt;span class="lit">0&lt;/span></code>
  </li>
  <li class="L3">
    <code>&lt;span class="pln">$ netcat &lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="pln">z &lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="pln">vv google&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="pln">com https&lt;/span></code>
  </li>
  <li class="L4">
    <code>&lt;span class="pln">DNS fwd&lt;/span>&lt;span class="pun">/&lt;/span>&lt;span class="pln">rev mismatch&lt;/span>&lt;span class="pun">:&lt;/span>&lt;span class="pln"> google&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="pln">com &lt;/span>&lt;span class="pun">!=&lt;/span>&lt;span class="pln"> maa03s16&lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="kwd">in&lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="pln">f2&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="lit">1e100&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="pln">net&lt;/span></code>
  </li>
  <li class="L5">
    <code>&lt;span class="pln">DNS fwd&lt;/span>&lt;span class="pun">/&lt;/span>&lt;span class="pln">rev mismatch&lt;/span>&lt;span class="pun">:&lt;/span>&lt;span class="pln"> google&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="pln">com &lt;/span>&lt;span class="pun">!=&lt;/span>&lt;span class="pln"> maa03s16&lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="kwd">in&lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="pln">f6&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="lit">1e100&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="pln">net&lt;/span></code>
  </li>
  <li class="L6">
    <code>&lt;span class="pln">DNS fwd&lt;/span>&lt;span class="pun">/&lt;/span>&lt;span class="pln">rev mismatch&lt;/span>&lt;span class="pun">:&lt;/span>&lt;span class="pln"> google&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="pln">com &lt;/span>&lt;span class="pun">!=&lt;/span>&lt;span class="pln"> maa03s16&lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="kwd">in&lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="pln">f5&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="lit">1e100&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="pln">net&lt;/span></code>
  </li>
  <li class="L7">
    <code>&lt;span class="pln">DNS fwd&lt;/span>&lt;span class="pun">/&lt;/span>&lt;span class="pln">rev mismatch&lt;/span>&lt;span class="pun">:&lt;/span>&lt;span class="pln"> google&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="pln">com &lt;/span>&lt;span class="pun">!=&lt;/span>&lt;span class="pln"> maa03s16&lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="kwd">in&lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="pln">f3&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="lit">1e100&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="pln">net&lt;/span></code>
  </li>
  <li class="L8">
    <code>&lt;span class="pln">DNS fwd&lt;/span>&lt;span class="pun">/&lt;/span>&lt;span class="pln">rev mismatch&lt;/span>&lt;span class="pun">:&lt;/span>&lt;span class="pln"> google&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="pln">com &lt;/span>&lt;span class="pun">!=&lt;/span>&lt;span class="pln"> maa03s16&lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="kwd">in&lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="pln">f8&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="lit">1e100&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="pln">net&lt;/span></code>
  </li>
  <li class="L9">
    <code>&lt;span class="pln">DNS fwd&lt;/span>&lt;span class="pun">/&lt;/span>&lt;span class="pln">rev mismatch&lt;/span>&lt;span class="pun">:&lt;/span>&lt;span class="pln"> google&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="pln">com &lt;/span>&lt;span class="pun">!=&lt;/span>&lt;span class="pln"> maa03s16&lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="kwd">in&lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="pln">f0&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="lit">1e100&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="pln">net&lt;/span></code>
  </li>
  <li class="L0">
    <code>&lt;span class="pln">DNS fwd&lt;/span>&lt;span class="pun">/&lt;/span>&lt;span class="pln">rev mismatch&lt;/span>&lt;span class="pun">:&lt;/span>&lt;span class="pln"> google&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="pln">com &lt;/span>&lt;span class="pun">!=&lt;/span>&lt;span class="pln"> maa03s16&lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="kwd">in&lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="pln">f7&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="lit">1e100&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="pln">net&lt;/span></code>
  </li>
  <li class="L1">
    <code>&lt;span class="pln">DNS fwd&lt;/span>&lt;span class="pun">/&lt;/span>&lt;span class="pln">rev mismatch&lt;/span>&lt;span class="pun">:&lt;/span>&lt;span class="pln"> google&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="pln">com &lt;/span>&lt;span class="pun">!=&lt;/span>&lt;span class="pln"> maa03s16&lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="kwd">in&lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="pln">f4&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="lit">1e100&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="pln">net&lt;/span></code>
  </li>
  <li class="L2">
    <code>&lt;span class="pln">google&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="pln">com &lt;/span>&lt;span class="pun">[&lt;/span>&lt;span class="lit">74.125&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="lit">236.162&lt;/span>&lt;span class="pun">]&lt;/span> &lt;span class="lit">443&lt;/span> &lt;span class="pun">(&lt;/span>&lt;span class="pln">https&lt;/span>&lt;span class="pun">)&lt;/span>&lt;span class="pln"> open&lt;/span></code>
  </li>
  <li class="L3">
    <code>&lt;span class="pln"> sent &lt;/span>&lt;span class="lit">0&lt;/span>&lt;span class="pun">,&lt;/span>&lt;span class="pln"> rcvd &lt;/span>&lt;span class="lit">0&lt;/span></code>
  </li>
  <li class="L4">
    <code>&lt;span class="pln">$ netcat &lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="pln">v &lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="pln">z &lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="pln">n &lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="kwd">w&lt;/span> &lt;span class="lit">1&lt;/span> &lt;span class="lit">192.168&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="lit">1.254&lt;/span> &lt;span class="lit">1&lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="lit">1023&lt;/span></code>
  </li>
  <li class="L5">
    <code>&lt;span class="pun">(&lt;/span>&lt;span class="pln">UNKNOWN&lt;/span>&lt;span class="pun">)&lt;/span> &lt;span class="pun">[&lt;/span>&lt;span class="lit">192.168&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="lit">1.254&lt;/span>&lt;span class="pun">]&lt;/span> &lt;span class="lit">989&lt;/span> &lt;span class="pun">(&lt;/span>&lt;span class="pln">ftps&lt;/span>&lt;span class="pun">-&lt;/span>&lt;span class="pln">data&lt;/span>&lt;span class="pun">)&lt;/span>&lt;span class="pln"> open&lt;/span></code>
  </li>
  <li class="L6">
    <code>&lt;span class="pun">(&lt;/span>&lt;span class="pln">UNKNOWN&lt;/span>&lt;span class="pun">)&lt;/span> &lt;span class="pun">[&lt;/span>&lt;span class="lit">192.168&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="lit">1.254&lt;/span>&lt;span class="pun">]&lt;/span> &lt;span class="lit">443&lt;/span> &lt;span class="pun">(&lt;/span>&lt;span class="pln">https&lt;/span>&lt;span class="pun">)&lt;/span>&lt;span class="pln"> open&lt;/span></code>
  </li>
  <li class="L7">
    <code>&lt;span class="pun">(&lt;/span>&lt;span class="pln">UNKNOWN&lt;/span>&lt;span class="pun">)&lt;/span> &lt;span class="pun">[&lt;/span>&lt;span class="lit">192.168&lt;/span>&lt;span class="pun">.&lt;/span>&lt;span class="lit">1.254&lt;/span>&lt;span class="pun">]&lt;/span> &lt;span class="lit">53&lt;/span> &lt;span class="pun">(&lt;/span>&lt;span class="pln">domain&lt;/span>&lt;span class="pun">)&lt;/span>&lt;span class="pln"> open&lt;/span></code>
  </li>
</ol>

也可以看看 ：

  * [使用 nmap 命令扫描网络中开放的端口](https://linux.cn/article-2561-1.html)。
  * 手册页 &#8211; <a class="ext" href="http://www.manpager.com/linux/man1/nc.1.html" target="_blank" rel="external nofollow">nc(1)</a>, <a class="ext" href="http://www.manpager.com/linux/man1/nmap.1.html" target="_blank" rel="external nofollow">nmap(1)</a>

* * *

via: <a class="ext" href="http://www.cyberciti.biz/faq/linux-port-scanning/" target="_blank" rel="external nofollow">http://www.cyberciti.biz/faq/linux-port-scanning/</a>

作者：Vivek Gite 译者：<a class="ext" href="https://github.com/strugglingyouth" target="_blank" rel="external nofollow">strugglingyouth</a> 校对：<a class="ext" href="https://github.com/wxy" target="_blank" rel="external nofollow">wxy</a>

本文由 <a class="ext" href="https://github.com/LCTT/TranslateProject" target="_blank" rel="external nofollow">LCTT</a> 原创编译，[Linux中国](https://linux.cn/article-6733-1.html) 荣誉推出