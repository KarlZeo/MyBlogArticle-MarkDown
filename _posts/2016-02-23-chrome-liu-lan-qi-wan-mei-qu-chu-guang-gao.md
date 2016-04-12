---
id: 312
title: chrome 浏览器完美去除广告
date: 2016-02-23T17:27:21+08:00
author: Kanaan Austen
layout: post
guid: https://blog.nieyujiang.info/?p=312
permalink: /2016/02/23/chrome-liu-lan-qi-wan-mei-qu-chu-guang-gao/
dsq_thread_id:
  - 4603010842
views:
  - 14
categories:
  - 黑科技
---
现在这个年头,广告越来越猖狂了.譬如某酷,广告动辄60s,120s, 让人气的想要砸电脑.最关键的是,尼玛放点有意义的广告也行啊,有事没事来个大天使之剑,谁受得了.

## 解决方法(首先需要你能出去玩耍) {#toc_0}

### 安装 ADBlock Plus 插件 {#toc_1}

ADBlock Plus 是一个神奇的插件,能够订阅不同的广告屏蔽规则,实现广告屏蔽.以下是我的订阅.
  
![](https://blog.nieyujiang.info/wp-content/uploads/2016/02/14561914585913.jpg "chrome 浏览器完美去除广告")￼
  
全部启动并更新,基本上 80% ~ 90% 的页面广告都能去掉.

### 安装 ADfree.Player.Online 插件 {#toc_2}

这又是一个神奇的插件.可以完美屏蔽各种视屏广告.装上更新一下规则就可以用.

### 如果你使用 SwitchyOmega 等等代理插件(请继续往下看) {#toc_3}

ADFree 这个插件默认使用的是代理,与 SwitchyOmega 冲突.想要共存需要关闭代理控制.
  
![](https://blog.nieyujiang.info/wp-content/uploads/2016/02/14561925728595.jpg "chrome 浏览器完美去除广告")￼
  
1、新建情景模式-情景模式名称：ADfree，情景模式的类型为“Proxy服务器”；
    
![](https://blog.nieyujiang.info/wp-content/uploads/2016/02/14561927052450.jpg "chrome 浏览器完美去除广告")￼

Proxy协议为：HTTP；Proxy服务器为：yk.pp.navi.youku.com；Proxy端口：80。
    
![](https://blog.nieyujiang.info/wp-content/uploads/2016/02/14561927155560.jpg "chrome 浏览器完美去除广告")￼

2、自动切换-切换规则-增加条件：
  
条件类型为：“网址正则”；条件设置为：<sup>http:\/\/[<sup>\/]+\/crossdomain.xml；情景模式选择：ADfree。</sup></sup>
  
![](https://blog.nieyujiang.info/wp-content/uploads/2016/02/14561927263961.jpg "chrome 浏览器完美去除广告")￼

### 搞定 {#toc_4}