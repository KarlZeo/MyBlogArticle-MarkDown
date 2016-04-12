---
id: 377
title: pip介绍与使用
date: 2016-04-03T17:37:13+08:00
author: Kanaan Austen
layout: post
guid: https://blog.nieyujiang.info/?p=377
permalink: /2016/04/03/pip-jie-shao-yu-shi-yong/
views:
  - 25
dsq_thread_id:
  - 4715388092
categories:
  - Linux
---
<!--wp-compress-html-->

<!--wp-compress-html no compression-->

## 1. 介绍 {#toc_0}

pip 是一个安装和管理 Python 包的工具，python安装包的工具有easy\_install, setuptools, pip，distribute。使用这些工具都能下载并安装django。，而pip是easy\_install的替代品。在CPython解释器，pypy解释器，可以很好地工作

## 2. 使用 {#toc_1}

### 2.1 安装pip {#toc_2}

安装和升级之前，先下载 [get-pip.py](https://bootstrap.pypa.io/get-pip.py)
  
然后使用下面的命令：

<pre class="prettyprint" ><code>python get-pip.py
</code></pre>

不过注意一下，linux或osX下，需要权限，使用下面的命令，输入密码后即可。

<pre class="prettyprint" ><code>sudo python get-pip.py 
</code></pre>

windows下需要管理员权限启动终端。
  
如果你还没有安装了setuptools，get-pip.py 会帮你安装。
  
如果你已经安装了setuptools，运行下面的命令进行升级。

<pre class="prettyprint" ><code>pip install -U setuptools
</code></pre>

windows下，注意将pip路劲加到系统的path中，原因就不解释了吧。

### 2.2 升级pip {#toc_3}

Linux or OS X系统，运行下面的命令:

<pre class="prettyprint" ><code>pip install -U pip
</code></pre>

windows系统运行下面的命令：

<pre class="prettyprint" ><code>python -m pip install -U pip
</code></pre>

### 2.3 安装包 {#toc_4}

使用下面的命令来安装包

<pre class="prettyprint" ><code>pip install SomePackage            # latest version
pip install SomePackage==1.0.4     # specific version
pip install &#39;SomePackage&gt;=1.0.4&#39;     # minimum version
</code></pre>

要看更多地例子，可以看这里 `pip install`

例如我要安装Django，用下面的一条命令即可，方便快捷。

<pre class="prettyprint" ><code>pip install Django==1.7
</code></pre>

<!--wp-compress-html no compression-->

<!--wp-compress-html-->