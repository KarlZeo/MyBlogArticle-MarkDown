---
id: 213
title: UINavigationController 设置“返回”“back”
date: 2016-02-19T22:56:01+08:00
author: Kanaan Austen
layout: post
guid: https://blog.nieyujiang.info/?p=213
permalink: /2016/02/19/uinavigationcontroller-setting-back-back/
views:
  - 16
dsq_thread_id:
  - 4713909132
categories:
  - OC
---
&nbsp;

  1. 在之前控制器 添加语句

初始化界面时候

//设置返回按钮

UIBarButtonItem *backItem = [[UIBarButtonItem alloc] init];

backItem.title = @”返回”;

self.navigationItem.backBarButtonItem = backItem;
  
2. 这时候后面的控制器 “back”按钮自动就变成刚刚 设置的 “返回”了