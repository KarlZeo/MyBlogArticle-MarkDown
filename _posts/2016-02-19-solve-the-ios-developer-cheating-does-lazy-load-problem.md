---
id: 265
title: 解决 iOS 开发者坑爹的懒加载不执行的问题
date: 2016-02-19T23:08:57+08:00
author: Kanaan Austen
layout: post
guid: https://blog.nieyujiang.info/?p=265
permalink: /2016/02/19/solve-the-ios-developer-cheating-does-lazy-load-problem/
dsq_thread_id:
  - 4594785844
flavour_num_words:
  - 11
views:
  - 9
categories:
  - OC
---
<!--wp-compress-html-->

<!--wp-compress-html no compression-->

我也不知什么原因,懒加载的方法代码明明是正确的,然而就是不执行.

#### 解决方案

<pre class="prettyprint" ><code>在- (void)viewDidLoad 方法里面手动执行一下懒加载的方法.
</code></pre>

<!--wp-compress-html no compression-->

<!--wp-compress-html-->