---
id: 343
title: Adobe 系列 PJ 全过程
date: 2016-03-13T02:41:44+08:00
author: Kanaan Austen
layout: post
guid: https://blog.nieyujiang.info/?p=343
permalink: /2016/03/13/adobe-xi-lie-pj-quan-guo-cheng/
dsq_thread_id:
  - 4675488421
views:
  - 12
categories:
  - Mac
  - Windows
---
<!--wp-compress-html-->

<!--wp-compress-html no compression-->

## 下载注册机 {#toc_0}

推荐使用`X-Force注册机`.请自行搜索.

## 安装 {#toc_1}

1、禁用网络或者拔掉网线,确保Hosts中没有127.0.0.1 lmlicenses.wip4.adobe.com，127.0.0.1 lm.licenses.adobe.com等关于Adobe的屏蔽

PS：如果之前安装注册失败，确保删掉下面两个文件夹，然后重新安装

Win:

<pre class="prettyprint" ><code>C:\Program Files (x86)\Common Files\Adobe\SLCache
C:\ProgramData\Adobe\SLStore
</code></pre>

Mac:

<pre class="prettyprint" ><code>/Library/Application Support/Adobe/SLStore

/Library/Application Support/Adobe/SLCache
</code></pre>

2、安装Adobe CC,同时打开注册机Keygen(整个过程都不要关闭),点击安装(Install)，点击登录(Sign In)，点击稍后连接(Connect Later)，接受许可后输入注册机生成的序列号(点击注册机generate生成序列号，然后填入)，点击Please connect to the internet and retry

2.1、安装升级更新包(如从CC 2014升级到CC 2014.2)

3、启动任意一个软件，PS或者AI都行

4、点击“网络连接有问题？(Having trouble connecting to the internet ?)”，然后点击离线激活(Offline Activation)

5、点击注册机的Generate a requets Code，复制填入激活

6、软件成功启动后关闭

7、手动在Hosts中加( C:\Windows\System32\drivers\etc\hosts)

<pre class="prettyprint" ><code>127.0.0.1 activate.adobe.com
127.0.0.1 ereg.adobe.com
127.0.0.1 hlrcv.stage.adobe.com
127.0.0.1 lm.licenses.adobe.com
127.0.0.1 lmlicenses.wip4.adobe.com
127.0.0.1 na1r.services.adobe.com
127.0.0.1 na2m-pr.licenses.adobe.com
127.0.0.1 practivate.adobe.com
127.0.0.1 wip.adobe.com
</code></pre>

<!--wp-compress-html no compression-->

<!--wp-compress-html-->