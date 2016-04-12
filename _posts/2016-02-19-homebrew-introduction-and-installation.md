---
id: 25
title: Homebrew简介及安装
date: 2016-02-19T20:59:18+08:00
author: Kanaan Austen
layout: post
guid: https://blog.nieyujiang.info/?p=25
permalink: /2016/02/19/homebrew-introduction-and-installation/
dsq_thread_id:
  - 4670377593
views:
  - 8
categories:
  - Mac
---
<!--wp-compress-html-->

<!--wp-compress-html no compression-->

**Homebrew是神马**

linux系统有个让人蛋疼的通病，软件包依赖，好在当前主流的两大发行版本都自带了解决方案，Red hat有yum，Ubuntu有apt-get

神马，你用mac os，不好意Mac os木有类似的东东，泪奔中几经折腾总算找到了第三方支持：Homebrew，Homebrew简称brew，是Mac OSX上的软件包管理工具，能在Mac中方便的安装软件或者卸载软件，可以说Homebrew就是mac下的apt-get、yum神器

**Homebrew安装**

Homebrew的安装非常简单，打开终端复制、粘贴以下命令，回车，搞定(请放心使用，原汁原味的官方安装方法搬运）

<pre class="prettyprint" ><code>ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
</code></pre>

ps:不知道为什么执行这个命令有时会返回400，估计可能被墙了，过几分钟重试下一般就ok了.

**Homebrew使用**

Homebrew使用没啥好说的了，常用的

搜索软件：brew search 软件名，如brew search wget

安装软件：brew install 软件名，如brew install wget

卸载软件：brew remove 软件名，如brew remove wget

更多的？自己去官网挖吧 **<http://brew.sh/index_zh-cn.html>**

<!--wp-compress-html no compression-->

<!--wp-compress-html-->