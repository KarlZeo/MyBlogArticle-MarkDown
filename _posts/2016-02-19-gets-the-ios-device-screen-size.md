---
id: 166
title: 获取 ios 设备的屏幕大小
date: 2016-02-19T22:34:58+08:00
author: Kanaan Austen
layout: post
guid: https://blog.nieyujiang.info/?p=166
permalink: /2016/02/19/gets-the-ios-device-screen-size/
views:
  - 9
categories:
  - OC
---
<!--wp-compress-html-->

<!--wp-compress-html no compression-->

不多说,直接上代码.

<pre class="prettyprint" ><code>UIScreen *screen = [UIScreen mainScreen];

CGFloat screenW = screen. bounds. size. width;

CGFloat screenH = screen. bounds. size. height;

</code></pre>

<!--wp-compress-html no compression-->

<!--wp-compress-html-->