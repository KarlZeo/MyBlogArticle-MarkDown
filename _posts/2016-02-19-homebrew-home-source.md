---
id: 223
title: Homebrew国内源
date: 2016-02-19T22:59:41+08:00
author: Kanaan Austen
layout: post
guid: https://blog.nieyujiang.info/?p=223
permalink: /2016/02/19/homebrew-home-source/
dsq_thread_id:
  - 4652842425
views:
  - 15
categories:
  - Mac
---
<!--wp-compress-html-->

<!--wp-compress-html no compression-->

#### 配置镜像源

设置环境变量 HOMEBREW\_BOTTLE\_DOMAIN 即可使用本镜像源加速下载 Homebrew 资源。

#### bash

在 `~/.bashrc` 中加入

<pre class="prettyprint" ><code>export HOMEBREW_BOTTLE_DOMAIN=http://7xkcej.dl1.z0.glb.clouddn.com
</code></pre>

#### fish

在 `~/.config/fish/config.fish` 中加入

<pre class="prettyprint" ><code>set -x HOMEBREW_BOTTLE_DOMAIN http://7xkcej.dl1.z0.glb.clouddn.com
</code></pre>

#### 配置 Git 源（可选）

Homebrew 仓库默认托管在 GitHub 上，但是国内连接 GitHub 也不是很稳定，所以同样镜像了一份 Git 仓库到 GitCafe。 要使用 GitCafe 仓库源请运行一下命令：

<pre class="prettyprint" ><code>cd /usr/local git remote set-url origin https://gitcafe.com/ban-ninja/homebrew.git
</code></pre>

#### 说明

本镜像源使用七牛云存储来加速，每十分钟同步一次 本镜像源只镜像了 Homebrew 托管在 Bintray 上的二进制预编译包，所以只对这些二进制包有加速功能（Homebrew 大部分情况下使用该渠道下载安装软件）。 GitCafe 上的 Homebrew 仓库同样是每十分钟同步一次

<!--wp-compress-html no compression-->

<!--wp-compress-html-->