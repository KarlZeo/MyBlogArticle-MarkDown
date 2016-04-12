---
id: 241
title: 升级 Oh My Zsh 报错
date: 2016-02-19T23:03:02+08:00
author: Kanaan Austen
layout: post
guid: https://blog.nieyujiang.info/?p=241
permalink: /2016/02/19/upgrades-oh-my-zsh-errors/
dsq_thread_id:
  - 4700193094
views:
  - 19
categories:
  - Mac
---
<!--wp-compress-html-->

<!--wp-compress-html no compression-->

错误代码

<pre class="prettyprint" ><code>error: Cannot pull with rebase: You have unstaged changes. There was an error updating. Try again later?
</code></pre>

解决方案

<pre class="prettyprint" ><code>cd "$ZSH" && git stash && upgrade_oh_my_zsh
</code></pre>

got it!

<!--wp-compress-html no compression-->

<!--wp-compress-html-->