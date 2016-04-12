---
id: 382
title: 清除 Xcode 项目缓存
date: 2016-04-10T22:27:11+08:00
author: Kanaan Austen
layout: post
guid: https://blog.nieyujiang.info/?p=382
permalink: /2016/04/10/qing-chu-xcode-xiang-mu-huan-cun/
views:
  - 3
categories:
  - Mac
---
<!--wp-compress-html-->

<!--wp-compress-html no compression-->

运行错误、编译错误、发布错误可尝试清除 Xcode 缓存；清除 Xcode 缓存也能减少占用磁盘空间。

（1）前往文件夹，删除里面的文件：

<pre class="prettyprint" ><code>/Users/用户名/Library/Developer/Xcode/DerivedData/
</code></pre>

 
  
（2）同时也可在 Xcode 里点击菜单 “Product” -> “Clean” ，效果更佳
  
 
  
PS：如果想删除所有模拟器安装测试的 App 数据，一般更新 Xcode 版本可能有所需要（非必须的）。
  
可以前往文件夹，删除里面的文件：

<pre class="prettyprint" ><code>/Users/用户名/Library/Developer/CoreSimulator/Devices/
</code></pre>

<!--wp-compress-html no compression-->

<!--wp-compress-html-->