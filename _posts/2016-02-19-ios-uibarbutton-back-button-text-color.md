---
id: 259
title: iOS UIBarButton back button 文字颜色
date: 2016-02-19T23:07:30+08:00
author: Kanaan Austen
layout: post
guid: https://blog.nieyujiang.info/?p=259
permalink: /2016/02/19/ios-uibarbutton-back-button-text-color/
flavour_num_words:
  - 44
dsq_thread_id:
  - 4595339958
views:
  - 9
categories:
  - OC
---
<!--wp-compress-html-->

<!--wp-compress-html no compression-->

系统默认的颜色是蓝色,蓝色不难看,但是在某些底色比较重的背景上面,蓝色就很难分辨了.更改方法很简单,在

<pre class="prettyprint" ><code>AppDelegate.m
</code></pre>

这个文件的

<pre class="prettyprint" ><code>- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:
(NSDictionary *)launchOptions
</code></pre>

方法里面,加入一句话就可以搞定.

<pre class="prettyprint" ><code>[[UINavigationBar appearance] setTintColor:[UIColor whiteColor]];
</code></pre>

**OK**

**Enjoy it!**

<!--wp-compress-html no compression-->

<!--wp-compress-html-->