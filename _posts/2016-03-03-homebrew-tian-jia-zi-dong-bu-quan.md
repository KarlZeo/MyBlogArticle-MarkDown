---
id: 322
title: Homebrew 添加自动补全
date: 2016-03-03T01:45:03+08:00
author: Kanaan Austen
layout: post
guid: https://blog.nieyujiang.info/?p=322
permalink: /2016/03/03/homebrew-tian-jia-zi-dong-bu-quan/
dsq_thread_id:
  - 4627096750
views:
  - 7
categories:
  - Mac
---
<!--wp-compress-html-->

<!--wp-compress-html no compression-->

Homebrew 是 OS X 上面的包管理,但是这个自动补全么&#8230;有点&#8230;

## 1.首先你要有个 Homebrew {#toc_0}

打开`terminal`,复制粘贴以下代码.
  
``<!--wp-compress-html-->

<!--wp-compress-html no compression-->

Homebrew 是 OS X 上面的包管理,但是这个自动补全么&#8230;有点&#8230;

## 1.首先你要有个 Homebrew {#toc_0}

打开`terminal`,复制粘贴以下代码.
  
`` 

## 2.安装 zsh {#toc_1}

<pre class="prettyprint" ><code>brew install zsh
</code></pre>

## 3.安装 oh my zsh {#toc_2}

使用 curl

<pre class="prettyprint" ><code>sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
</code></pre>

使用 wget

<pre class="prettyprint" ><code>sh -c "$(wget https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
</code></pre>

## 4.编辑`.zshrc`文件 {#toc_3}

添加插件支持,例如
  
```<!--wp-compress-html-->

<!--wp-compress-html no compression-->

Homebrew 是 OS X 上面的包管理,但是这个自动补全么&#8230;有点&#8230;

## 1.首先你要有个 Homebrew {#toc_0}

打开`terminal`,复制粘贴以下代码.
  
``<!--wp-compress-html-->

<!--wp-compress-html no compression-->

Homebrew 是 OS X 上面的包管理,但是这个自动补全么&#8230;有点&#8230;

## 1.首先你要有个 Homebrew {#toc_0}

打开`terminal`,复制粘贴以下代码.
  
`` 

## 2.安装 zsh {#toc_1}

<pre class="prettyprint" ><code>brew install zsh
</code></pre>

## 3.安装 oh my zsh {#toc_2}

使用 curl

<pre class="prettyprint" ><code>sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
</code></pre>

使用 wget

<pre class="prettyprint" ><code>sh -c "$(wget https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh -O -)"
</code></pre>

## 4.编辑`.zshrc`文件 {#toc_3}

添加插件支持,例如
  
``` 
  
plugins在 `~/.oh-my-zsh/plugins` 下可以找到.

## 5.重新加载 `.zshrc` 配置文件 {#toc_4}

<pre class="prettyprint" ><code>source .zshrc
</code></pre>

这时候 brew 等等就可以自动补全了.

<!--wp-compress-html no compression-->

<!--wp-compress-html-->