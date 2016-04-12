---
id: 261
title: Surge For Mac 使用方法
date: 2016-02-19T23:08:12+08:00
author: Kanaan Austen
layout: post
guid: https://blog.nieyujiang.info/?p=261
permalink: /2016/02/19/usage-surge-for-mac/
flavour_num_words:
  - 158
dsq_thread_id:
  - 4597549581
views:
  - 27
categories:
  - Mac
---
<!--wp-compress-html-->

<!--wp-compress-html no compression-->

Surge for Mac 是针对 Surge for iOS 用户的一项「福利」，这意味着你首先必须是 Surge for iOS 的用户才可以激活和使用 Mac 版，两者一脉相承，除了配置文件的命名和保存位置不同，在使用体验上非常一致。

Mac 版的下载地址和激活都需要通过 iOS 版来实现，打开 Surge for iOS，切换到「More」标签页，展开「Surge Mac」就能看到具体的激活步骤。需要注意的是下载地址区分大小写：
  
[点我下载](http://surge.run/Surge-Mac.zip)

显示出 Surge Mac Beta 的窍门，切换到 More 页面后还需要摇一摇，和摇红包姿势一样。

Mac 版配置文件和 iOS 版配置文件可以通用，不过 Mac 版不支持多服务器配置的#!PROXY-OVERRIDE 参数，所以需要在配置文件中写好具体的代理服务器地址，具体内容和 iOS 版的 Main.conf 基本一致，配置文件可以参考这里
  
[点我去看配置文件](https://gist.github.com/scomper/843577fe581c1d6df974)

<pre class="prettyprint" ><code>- 配置文件增加了 interface 和 port 两个字段，用来定义缺省的 IP 地址和端口，默认是 0.0.0.0 和 6152；
- 配置文件需要命名成 .surge.conf 放在「个人」目录下（也可以通过前往文件夹~/ 定位）；
- 启用 Surge 前，需要在「系统偏好设置 — 网络」中将 HTTP 和 HTTPS 的代理设置设置为 127.0.0.1:6152 。
-
</code></pre>

忽略这些主机与域的代理设置中（Proxy Bypass），至少要包含以下内容：

<pre class="prettyprint" ><code>127.0.0.1, 192.168.0.0/16, 10.0.0.0/8, 172.16.0.0/12, localhost, *.local
</code></pre>

配置文件命名成包含 . 前缀的文件 .surge.conf 会被视为隐藏的系统文件，所以要复制和修改它首先需要 Finder 显示系统文件.打开终端,输入以下代码.

<pre class="prettyprint" ><code>defaults write com.apple.finder AppleShowAllFiles YES

killall Finder

</code></pre>

然后重启 Finder. 即可看到隐藏文件.

Surge Mac 1.0.2开始支持自动更新。Surge 运行过程中如果修改了配置文件可以点击「Reload Configuration」重新加载。

和 iOS 版一样，Recent Requests 窗口中可以直观的查看到网络访问的情况，点击具体的条目弹出详细内容窗口。另外状态栏图标包含流量显示，看起来又可以少装一个 iStat Menus 的应用了。Surge for Mac 的日志保存在 ~/Library/Logs/Surge/ 目录下，通过系统的「控制台」可以进行具体的查看和排错定位。

如果希望开机就自动加载 Surge，可以到「系统偏好设置-用户与群组」中将 Surge 添加到「登录项」。

接下来就是最重要的一环,设置 ss 代理.很简单,把手机版的 proxy 抄过来就行.设置浏览器代理,把所有流量指向`127.0.0.1:6152`即可.

浏览器啥的搞定了, 但是`terminal` 里面的东西根本不吃这一套,解决办法很简单.在你的终端配置文件里面加入下面两条.

<pre class="prettyprint" ><code>export http_proxy=http://127.0.0.1:6152/
export https_proxy=http://127.0.0.1:6152/
</code></pre>

ok, 搞定了. ss 基本可以扔掉了.

<!--wp-compress-html no compression-->

<!--wp-compress-html-->