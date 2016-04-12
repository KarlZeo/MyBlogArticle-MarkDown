---
id: 229
title: Homebrew 隐藏命令
date: 2016-02-19T23:00:48+08:00
author: Kanaan Austen
layout: post
guid: https://blog.nieyujiang.info/?p=229
permalink: /2016/02/19/homebrew-hide-command/
dsq_thread_id:
  - 4652839742
views:
  - 14
categories:
  - Mac
---
<!--wp-compress-html-->

<!--wp-compress-html no compression-->

[Homebrew](http://brew.sh/) 可谓是 Mac 开发者必备的工具之一，它承载在各种包管理的特性以及拥有一票热情高涨的社区提供强大支持。今天我就给大家解密一下 brew 内部的隐藏命令都有哪些。

## 服务管理

当我们安装了众多需要挂载的服务，需要重启或停止的时候，都特别希望 Mac 可以有个统一的命令可以管理服务的状态，比如 `services` 命令甚至说 `/etc/init.d/` 也可以啊！

<pre class="prettyprint" ><code>brew services command [formula]

usage: [sudo] brew services [--help] &lt;command&gt; [&lt;formula&gt;]
Small wrapper around `launchctl` for supported formulae, commands available:

cleanup Get rid of stale services and unused plists
list List all services managed by `brew services`
restart Gracefully restart selected service
start Start selected service
stop Stop selected service

Options, sudo and paths:

sudo When run as root, operates on /Library/LaunchDaemons (run at boot!)
Run at boot: /Library/LaunchDaemons
Run at login: /Users/icyleaf/Library/LaunchAgents
</code></pre>

这个是我要讲的第一个隐藏命令！太坑爹了，那么实用的命令居然没有包含在 `brew --help` 帮助里面！我们再也不用发愁记住 `launchctl load/unload &lt;path&gt;` 的坑爹命令了！

重启 Nigix 就那么简单：

<pre class="prettyprint" ><code>services restart nginx
</code></pre>

停止 Postgresql 服务

<pre class="prettyprint" ><code>services stop mysql
</code></pre>

查看系统通过 brew 安装的服务：

<pre class="prettyprint" ><code>brew services list
postgresql started - /Users/icyleaf/Library/LaunchAgents/homebrew.mxcl.postgresql.plist
nginx started - /Users/icyleaf/Library/LaunchAgents/homebrew.mxcl.nginx.plist
</code></pre>

清除已卸载无用的启动配置文件：

<pre class="prettyprint" ><code>brew services cleanup
Removing unused plist /Users/icyleaf/Library/LaunchAgents/homebrew.mxcl.mysql.plist
Removing unused plist /Users/icyleaf/Library/LaunchAgents/homebrew.mxcl.redis.plist

</code></pre>

## 安装扩展

这个相信很多人都已经用到过了，安装他人扩展的 brew 服务。由于 brew 和包含的包源都是通过 github 来管理，人为的维护管理，除了自己的源还允许别人的源添加进来。类似与 `Ubuntu` 的 `ppa`。好处在于只有我安装规定的方式把包丢到 github 上面就可以用了！

<pre class="prettyprint" ><code>brew tap &lt;gihhub_user/repo&gt;

</code></pre>

这个命令并没有包含任何的帮助说明，其实它只接受上面的这个参数。

举例说明一下，Mac OS 比较歧视 PHP ，所以每次系统更新都会把常用的开发包（Ruby、Python 等）也顺带着更新到最新版本。（吐槽：Java 都已经被抛弃不再默认安装了），而 `brew` 居然也不包含 `PHP` 的包，那怎么办呢？

<pre class="prettyprint" ><code>brew tap josegonzalez/php
</code></pre>

命令完成之后，执行（当前最新是 php 5.5 版本，请根据需要替换）

<pre class="prettyprint" ><code>brew install php55

</code></pre>

当我们没有传递任何参数，默认显示已经通过 `tap` 安装了哪些扩展，为什么我说是通过 `tap` 呢，因为 `brew` 其实除了这些自身也用了一些其他扩展，通过下面命令显示：

<pre class="prettyprint" ><code>brew ls-taps
</code></pre>

## Web 化显示可用包和已安装工具

对于习惯命令行的人这个用途不大，就顺带一提而已，这个命令依赖 `sinatra`，大家通过 `gem` 安装即可。

<pre class="prettyprint" ><code>brew server
```如果你用 `puma` 可能报一个 **[BUG] Segmentation fault** 错误，那是因为你通过 rvm 或 renv 安装了跟高级的版本，而系统却用的 1.8.7 造成了版本差，请切换为系统依赖后再重试（你可能需要重新安装 sinata）：
</code></pre>

rvm usesystem$ /usr/bin/gem install sinatra

<pre class="prettyprint" ><code>## 彩蛋
</code></pre>

brew beer

<pre class="prettyprint" ><code>## 更多隐藏命令

一次性没太多精力完解读所有隐藏命令，这个艰巨的任务就交给大家了：
</code></pre>

brew commands
  
&#8220;\`

</td></tr></tbody></table></figure>其实这些命令可以在[官方源代码](https://github.com/Homebrew/homebrew/tree/master/Library/Contributions/cmd)看到。

<!--wp-compress-html no compression-->

<!--wp-compress-html-->