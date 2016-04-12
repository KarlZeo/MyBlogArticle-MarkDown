---
id: 104
title: Xcode 7免证书真机调试
date: 2016-02-19T22:27:02+08:00
author: Kanaan Austen
layout: post
guid: https://blog.nieyujiang.info/?p=104
permalink: /2016/02/19/xcode-7-free-certificate-prototype-debugging/
dsq_thread_id:
  - 4635820688
views:
  - 18
categories:
  - iOS 编程
---
在Xcode 7中，苹果改变了自己在许可权限上的策略，此前Xcode只开放给注册开发者下载，但Xcode 7改变了这种惯有的做法，无需注册开发者账号，仅使用普通的Apple ID就能下载和上手体验。此前开发者需每年支付99美元的费用成为注册开发者才能在iPhone和iPad真机上运行代码，苹果新的开发者计划则放宽要求，无需购买，只要你感兴趣同样可以在设备上测试app。
  
如果你打算向App Store提交应用，那仍然需要付费。
  
使用方法:
  
1.新建一个普通的项目
  
2.进入xcode，菜单栏选择xcode –> preferences （快捷键 command + ,）
  
<img class="BDE_Image" title="" src="https://blog.nieyujiang.info/wp-content/uploads/2016/02/a5dfd55a703b7de0c26b6a8974ac300a.jpg" alt="Xcode 7免证书真机调试" title="Xcode 7免证书真机调试" alt="" width="560" height="423" />

3.在Accounts选项卡添加自己的Apple ID。
  
添加完成后你会看到这样的信息。
  
<img class="BDE_Image" src="https://blog.nieyujiang.info/wp-content/uploads/2016/02/090ac323983874520794ec2f0ef20302.jpg" alt="Xcode 7免证书真机调试" title="Xcode 7免证书真机调试" alt="" width="560" height="429" />

可以看到下面显示了iOS和Mac的Free标记了，在这之前是没有这些标记的。
  
4.生成证书。
  
点击View Details。会出现图一的样式。
  
点中间的“+”号按钮，弹出菜单中选择iOS Development，然后稍等片刻（正常情况下），Xcode就会帮你生成好Dev模式需要的certificate了
  
<img class="BDE_Image" src="https://blog.nieyujiang.info/wp-content/uploads/2016/02/924340905386195f70d10f7f8efb2725.jpg" alt="Xcode 7免证书真机调试" title="Xcode 7免证书真机调试" alt="" width="560" height="506" />

<img class="BDE_Image" src="https://blog.nieyujiang.info/wp-content/uploads/2016/02/561d5e551dfe6ebb8471e47edc9f8aa3.jpg" alt="Xcode 7免证书真机调试" title="Xcode 7免证书真机调试" alt="" width="560" height="506" />

5.在项目target的General页的Team中选中刚才Apple ID对应的项。
  
<img class="BDE_Image" src="https://blog.nieyujiang.info/wp-content/uploads/2016/02/70f01649e9166df5f0343faf9fa0fbf2.jpg" alt="Xcode 7免证书真机调试" title="Xcode 7免证书真机调试" alt="" width="560" height="284" />

6.添加Provisioning Profile.
  
在刚才选择Team的下面弹出的Issue下面，点Fix。一切就都由Xcode搞定了。
  
<img class="BDE_Image" src="https://blog.nieyujiang.info/wp-content/uploads/2016/02/3fd2980e1403ba5beb9c551cdb7c2139.jpg" alt="Xcode 7免证书真机调试" title="Xcode 7免证书真机调试" alt="" width="560" height="277" />

7.运行。
  
运行的时候这里可能会再手机上出现一个“不受信任的开发者”的提示。
  
<img class="BDE_Image" src="https://blog.nieyujiang.info/wp-content/uploads/2016/02/ec0551fb7d250d3304c6dbd36a2bd14a.jpg" alt="Xcode 7免证书真机调试" title="Xcode 7免证书真机调试" alt="" width="560" height="994" />

“设置” – “通用” – “描述文件”
  
<img class="BDE_Image" src="https://blog.nieyujiang.info/wp-content/uploads/2016/02/f8bcedc7d6182feee3de5449f369eef6.jpg" alt="Xcode 7免证书真机调试" title="Xcode 7免证书真机调试" alt="" width="560" height="994" />

“开发者账号”
  
<img class="BDE_Image" src="https://blog.nieyujiang.info/wp-content/uploads/2016/02/92c697b9387cbd6f3ec65b4aa7a2a694.jpg" alt="Xcode 7免证书真机调试" title="Xcode 7免证书真机调试" alt="" width="560" height="994" />

“信任开发者账号”
  
<img class="BDE_Image" src="https://blog.nieyujiang.info/wp-content/uploads/2016/02/84dbad82ba0c803adfcd070a4cfb1df9.jpg" alt="Xcode 7免证书真机调试" title="Xcode 7免证书真机调试" alt="" width="560" height="994" />

“信任”
  
<img class="BDE_Image" src="https://blog.nieyujiang.info/wp-content/uploads/2016/02/0db5fa2e20b276fe187d038d00d9c310.jpg" alt="Xcode 7免证书真机调试" title="Xcode 7免证书真机调试" alt="" width="560" height="994" />

最后就能跑起来啦！！！
  
<img class="BDE_Image" src="https://blog.nieyujiang.info/wp-content/uploads/2016/02/e4adeb71da4ffda50a2d96b3966701ef.jpg" alt="Xcode 7免证书真机调试" title="Xcode 7免证书真机调试" alt="" width="560" height="994" />