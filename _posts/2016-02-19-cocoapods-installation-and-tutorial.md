---
id: 245
title: CocoaPods安装和使用教程
date: 2016-02-19T23:03:49+08:00
author: Kanaan Austen
layout: post
guid: https://blog.nieyujiang.info/?p=245
permalink: /2016/02/19/cocoapods-installation-and-tutorial/
dsq_thread_id:
  - 4594761642
views:
  - 7
categories:
  - iOS 编程
---
<!--wp-compress-html-->

<!--wp-compress-html no compression-->

###CocoaPods是什么？
  
当你开发iOS应用时，会经常使用到很多第三方开源类库，比如JSONKit，AFNetWorking等等。可能某个类库又用到其他类库，所以要使用它，必须得另外下载其他类库，而其他类库又用到其他类库，“子子孙孙无穷尽也”，这也许是比较特殊的情况。总之就是，手动一个个去下载所需类库十分麻烦。另外一种常见情况是，你项目中用到的类库有更新，你必须得重新下载新版本，重新加入到项目中，十分麻烦。如果能有什么工具能解决这些恼人的问题，那将“善莫大焉”。所以，你需要 CocoaPods。

CocoaPods应该是iOS最常用最有名的类库管理工具了，上述两个烦人的问题，通过cocoaPods，只需要一行命令就可以完全解决，当然前提是你必须正确设置它。重要的是，绝大部分有名的开源类库，都支持CocoaPods。所以，作为iOS程序员的我们，掌握CocoaPods的使用是必不可少的基本技能了。

###如何下载和安装CocoaPods？
  
在安装CocoaPods之前，首先要在本地安装好Ruby环境。至于如何在Mac中安装好Ruby环境，请google一下，本文不再涉及。

假如你在本地已经安装好Ruby环境，那么下载和安装CocoaPods将十分简单，只需要一行命令。在Terminator（也就是终端）中输入以下命令

<pre class="prettyprint" ><code>sudo gem install cocoapods
</code></pre>

但是，且慢。如果你在天朝，在终端中敲入这个命令之后，会发现半天没有任何反应。原因无他，因为那堵墙阻挡了cocoapods.org。

但是，是的，又但是（不过是个可喜的“但是”）。我们可以用淘宝的Ruby镜像来访问cocoapods。按照下面的顺序在终端中敲入依次敲入命令：

<pre class="prettyprint" ><code>$ gem sources --remove https://rubygems.org/ --add https://ruby.taobao.org/
</code></pre>

为了验证你的Ruby镜像是并且仅是taobao，可以用以下命令查看：

<pre class="prettyprint" ><code>$ gem sources -l
</code></pre>

只有在终端中出现下面文字才表明你上面的命令是成功的：

<pre class="prettyprint" ><code>*** CURRENT SOURCES ***

https://ruby.taobao.org/
</code></pre>

这时候，你再次在终端中运行：

<pre class="prettyprint" ><code>sudo gem install cocoapods
</code></pre>

等上十几秒钟，CocoaPods就可以在你本地下载并且安装好了，不再需要其他设置。

###如何使用CocoaPods？
  
安装完成后,首先执行下面这句话

<pre class="prettyprint" ><code>pod setup
</code></pre>

然后就是等待,过一阵子就会把远程服务器的类库信息给同步下来.
  
这时候,你就可以正常使用 cocoapods 来管理你的类库了.

####在工程中初始化 podfile
  
进入你的工程目录
  
然后执行

<pre class="prettyprint" ><code>pod init
</code></pre>

然后选择一个你喜欢的文本编辑器,打开生成的 podfile 文件,加入你需要的类库.
  
保存完毕后执行下面这条命令

<pre class="prettyprint" ><code>pod install
</code></pre>

最后,会生成一个`.xcworkspace`结尾的文件,打开这个,以后就用这个来启动 xcode 即可.

<!--wp-compress-html no compression-->

<!--wp-compress-html-->