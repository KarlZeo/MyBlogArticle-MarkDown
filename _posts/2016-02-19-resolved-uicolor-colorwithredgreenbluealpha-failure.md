---
id: 198
title: '解决[UIColor colorWithRed: green: blue: alpha:] 失效问题'
date: 2016-02-19T22:51:50+08:00
author: Kanaan Austen
layout: post
guid: https://blog.nieyujiang.info/?p=198
permalink: /2016/02/19/resolved-uicolor-colorwithredgreenbluealpha-failure/
dsq_thread_id:
  - 4672794523
views:
  - 9
categories:
  - OC
---
<!--wp-compress-html-->

<!--wp-compress-html no compression-->

在设置颜色是用[UIColor colorWithRed: green: blue: alpha:] 有时会遇到颜色不显示的问题，，，刚开始以为是设置的颜色值太过浅的原因，后来试了其他的颜色值发觉并不是这样的，网上搜索了一下，发现了问题的所在：RGB的颜色值范围都是在**0.0~1.0**之间的，并不是我们误认为的0~255。

错误用法：

<pre class="prettyprint" ><code>cell.temperature.backgroundColor = [UIColor colorWithRed:226 green:229 blue:229 alpha:1];
</code></pre>

正确用法：

<pre class="prettyprint" ><code>cell.temperature.backgroundColor = [UIColor colorWithRed:226.0/255 green:229.0/255 blue:229.0/255 alpha:1];

</code></pre>

<!--wp-compress-html no compression-->

<!--wp-compress-html-->