---
id: 249
title: 重置 Mac 端 MySQL root 密码
date: 2016-02-19T23:04:31+08:00
author: Kanaan Austen
layout: post
guid: https://blog.nieyujiang.info/?p=249
permalink: /2016/02/19/reset-the-mac-side-mysql-root-password/
flavour_num_words:
  - 19
views:
  - 10
categories:
  - Mac
---
<!--wp-compress-html-->

<!--wp-compress-html no compression-->

在 Mac 端使用 brew 安装完 MySQL 后一开始是没有 root 密码的,保险起见,还是改一下 root 密码比较好.

<pre class="prettyprint" ><code>mysqladmin -u root -p password
</code></pre>

然后输入旧密码,新密码,重复输入新密码就 OK 了.

<!--wp-compress-html no compression-->

<!--wp-compress-html-->