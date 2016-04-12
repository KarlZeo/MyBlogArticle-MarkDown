---
id: 217
title: 这是一个令人忧伤的软件——看看你的微信好友谁删除你了
date: 2016-02-19T22:57:14+08:00
author: Kanaan Austen
layout: post
guid: https://blog.nieyujiang.info/?p=217
permalink: /2016/02/19/this-is-a-sad-software-micro-letter-look-at-your-friend-who-removed-you/
dsq_thread_id:
  - 4608744457
views:
  - 6
categories:
  - 黑科技
---
<!--wp-compress-html-->

<!--wp-compress-html no compression-->

大家都加了很多微信好友吧，多到有些人你都不知道是谁了。不过最令人忧伤的是，也许你很在意的一个某个人，其实已经默默的删除你了。

微信并没有一个功能告诉你，谁已经残忍的删除你了，估计也是担心会破坏和谐。昨天运维帮发现了一个小[软件/脚本](https://github.com/0x5e/wechat-deleted-friends)，可以帮你揭开这个血淋淋的事实——看看谁把你删除了。

**警告：如引起心理不适，请勿追责本站和该软件作者。:D**

这是一个才发布几天的开源脚本，由 [0x5e](https://github.com/0x5e) 所开发。是使用 Python 所编写的，如担心安全问题，可以直接查看[源代码](https://github.com/0x5e/wechat-deleted-friends/blob/master/wdf.py)。

其原理就是使用微信网页版本的接口来新建群组，如果加不进来就是被删好友了（不要在该群组里讲话，别人是看不见的）。

目前还有些小问题，不过不伤大雅：

  * 结果好像有疏漏一小部分，原因不明……
  * 最终会遗留下一个只有自己的群组，需要手工删一下
  * 没试过被拉黑的情况

在此下载这个 Python 脚本： <https://github.com/0x5e/wechat-deleted-friends/blob/master/wdf.py>

然后在终端下以命令行运行：

<pre class="prettyprint" ><code>python wdf.py
</code></pre>

然后会弹出一个显示登录网页版微信的二维码窗口，用手机扫描登录。

然后一路按回车即可，最终会告诉你有多少“好友”残忍的删除了你——以后和他们划清界限！

_一路回车，就会发现真相_

<!--wp-compress-html no compression-->

<!--wp-compress-html-->