---
id: 177
title: 精简OS X Office 2016字体文件，为你的Mac节约3GB空间
date: 2016-02-19T22:44:25+08:00
author: Kanaan Austen
layout: post
guid: https://blog.nieyujiang.info/?p=177
permalink: /2016/02/19/streamline-office-2016-os-x-font-files-to-save-your-mac-3gb/
dsq_thread_id:
  - 4701582515
views:
  - 10
categories:
  - Mac
---
Ofiffce 2016 For [Mac](http://www.abclite.cn/tag/mac)难用不难用是一回事，但尼玛巨硬太缺德的就是每个APP都有同样的字体文件，无法像Windows版本那样共用一个字体库，这就导致了每次安装、更新Word/Excel/PPT的时候体积巨大，本来SSD的今天硬盘就比较精贵，所以只好相伴瘦身了。

1、打开终端，输入：

sudo bash -c “curl -s https://raw.githubusercontent.com/goodbest/OfficeThinner/master/OfficeThinner.sh | bash”

2、根据要求输入密码，回车，等待处理，一般需要1分钟左右。

3、然后检查是否瘦身成功，在应用程序里可以看到Office组件大小：

&nbsp;

注意：

  * 该脚本仅适用于Office 2016 For Mac，只测试了：Office 2016 15.16（151105） / 15.17（151206）
  * 使用需要您自担风险。
  * 详细了解终端执行后再操作。