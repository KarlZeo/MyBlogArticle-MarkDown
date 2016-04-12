---
id: 60
title: 使用Alcatraz来管理Xcode插件
date: 2016-02-19T21:52:34+08:00
author: Kanaan Austen
layout: post
guid: https://blog.nieyujiang.info/?p=60
permalink: /2016/02/19/use-alcatraz-managed-xcode-plug-in/
dsq_thread_id:
  - 4656110620
views:
  - 5
categories:
  - iOS 编程
---
<!--wp-compress-html-->

<!--wp-compress-html no compression-->

## 简介

Alcatraz 是一个帮你管理 Xcode 插件、模版以及颜色配置的工具。它可以直接集成到 Xcode 的图形界面中，让你感觉就像在使用 Xcode 自带的功能一样。

## 安装和删除

使用如下的命令行来安装 Alcatraz：

<pre class="lang:sh decode:true">mkdir -p ~/Library/Application\ Support/Developer/Shared/Xcode/Plug-ins; curl -L http://git.io/lOQWeA | tar xvz -C ~/Library/Application\ Support/Developer/Shared/Xcode/Plug-ins</pre>

如果你不想使用 Alcatraz 了，可以使用如下命令来删除：

<pre class="lang:sh decode:true ">rm -rf ~/Library/Application\ Support/Developer/Shared/Xcode/Plug-ins/Alcatraz.xcplugin  
rm -rf ~/Library/Application\ Support/Alcatraz</pre>

## 使用

安装成功后重启 Xcode，就可以在 Xcode 的顶部菜单中找到 Alcatraz，如下所示：<section class="post-content">

![](https://blog.nieyujiang.info/wp-content/uploads/2016/02/c831aed43f4ca5425d8c349dffee7b71.jpg "使用Alcatraz来管理Xcode插件")点击 “Package Manager”，即可启动插件列表页面，如下所示：</p> 

![](https://blog.nieyujiang.info/wp-content/uploads/2016/02/c3a048eec61469cb455ebc9ea0b0f889.jpg "使用Alcatraz来管理Xcode插件")

之后你可以在右上角搜索插件，对于想安装的插件，点击其左边的图标，即可下载安装，如下所示，我正在安装`KImageNamed`插件：

![](https://blog.nieyujiang.info/wp-content/uploads/2016/02/73d70b022d16a45004ef1aee898ff6b5.jpg "使用Alcatraz来管理Xcode插件")

安装完成后，再次点击插件左边的图标，可以将该插件删除。

## 插件路径 {#}

Xcode 所有的插件都安装在目录`~/Library/Application Support/Developer/Shared/Xcode/Plug-ins/`下，你也可以手工切换到这个目录来删除插件。</section> 

<!--wp-compress-html no compression-->

<!--wp-compress-html-->