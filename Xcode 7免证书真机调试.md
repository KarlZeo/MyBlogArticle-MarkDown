#Xcode 7免证书真机调试

在Xcode 7中，苹果改变了自己在许可权限上的策略，此前Xcode只开放给注册开发者下载，但Xcode 7改变了这种惯有的做法，无需注册开发者账号，仅使用普通的Apple ID就能下载和上手体验。此前开发者需每年支付99美元的费用成为注册开发者才能在iPhone和iPad真机上运行代码，苹果新的开发者计划则放宽要求，无需购买，只要你感兴趣同样可以在设备上测试app。
  
如果你打算向App Store提交应用，那仍然需要付费。
  
使用方法:
  
1.新建一个普通的项目
  
2.进入xcode，菜单栏选择xcode –> preferences （快捷键 command + ,）
  
![](https://raw.githubusercontent.com/KanaanAusten/MyPictures/master/a5dfd55a703b7de0c26b6a8974ac300a.png)


3.在Accounts选项卡添加自己的Apple ID。
  
添加完成后你会看到这样的信息。
  
![](https://raw.githubusercontent.com/KanaanAusten/MyPictures/master/090ac323983874520794ec2f0ef20302.png)


可以看到下面显示了iOS和Mac的Free标记了，在这之前是没有这些标记的。
  
4.生成证书。
  
点击View Details。会出现图一的样式。
  
点中间的“+”号按钮，弹出菜单中选择iOS Development，然后稍等片刻（正常情况下），Xcode就会帮你生成好Dev模式需要的certificate了
  
![](https://raw.githubusercontent.com/KanaanAusten/MyPictures/master/924340905386195f70d10f7f8efb2725.png)


![](https://raw.githubusercontent.com/KanaanAusten/MyPictures/master/561d5e551dfe6ebb8471e47edc9f8aa3.png)


5.在项目target的General页的Team中选中刚才Apple ID对应的项。
  
![](https://raw.githubusercontent.com/KanaanAusten/MyPictures/master/70f01649e9166df5f0343faf9fa0fbf2.png)


6.添加Provisioning Profile.
  
在刚才选择Team的下面弹出的Issue下面，点Fix。一切就都由Xcode搞定了。
  
![](https://raw.githubusercontent.com/KanaanAusten/MyPictures/master/3fd2980e1403ba5beb9c551cdb7c2139.png)


7.运行。
  
运行的时候这里可能会再手机上出现一个“不受信任的开发者”的提示。

![](https://raw.githubusercontent.com/KanaanAusten/MyPictures/master/ec0551fb7d250d3304c6dbd36a2bd14a.png)

“设置” – “通用” – “描述文件”
  
![](https://raw.githubusercontent.com/KanaanAusten/MyPictures/master/f8bcedc7d6182feee3de5449f369eef6.png)


“开发者账号”
  
![](https://raw.githubusercontent.com/KanaanAusten/MyPictures/master/92c697b9387cbd6f3ec65b4aa7a2a694.png)

“信任开发者账号”
  
![](https://raw.githubusercontent.com/KanaanAusten/MyPictures/master/84dbad82ba0c803adfcd070a4cfb1df9.png)


“信任”
  
![](https://raw.githubusercontent.com/KanaanAusten/MyPictures/master/0db5fa2e20b276fe187d038d00d9c310.png)


最后就能跑起来啦！！！
  
![](https://raw.githubusercontent.com/KanaanAusten/MyPictures/master/e4adeb71da4ffda50a2d96b3966701ef.png)


