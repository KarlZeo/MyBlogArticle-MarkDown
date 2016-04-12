---
id: 368
title: 检测Linux VPS 采用的是什么虚拟化技术
date: 2016-04-02T03:49:28+08:00
author: Kanaan Austen
layout: post
guid: https://blog.nieyujiang.info/?p=368
permalink: /2016/04/02/jian-celinux-vps-shixenopenvz-hai-shikvm-zhen-jia/
views:
  - 20
dsq_thread_id:
  - 4713144983
categories:
  - Linux
  - 黑科技
---
<!--wp-compress-html-->

<!--wp-compress-html no compression-->

## 1. 下载源代码 {#toc_0}

首先,先来[virt-what的源代码网站](https://people.redhat.com/%7Erjones/virt-what/files/)下载最新的 `virt-what` 源代码.
  
目前最新的版本是 `virt-what-1.15` .

<pre class="prettyprint" ><code>wget http://people.redhat.com/~rjones/virt-what/files/virt-what-1.15.tar.gz
</code></pre>

## 2. 编译安装 {#toc_1}

<pre class="prettyprint" ><code>tar zxvf virt-what-1.15.tar.gz
cd virt-what-1.15/
./configure
make
make install
</code></pre>

## 3. 检测 {#toc_2}

执行 `virt-what`命令,就会输出当前 VPS 的架构.

<pre class="prettyprint" ><code>virt-what
</code></pre>

<!--wp-compress-html no compression-->

<!--wp-compress-html-->