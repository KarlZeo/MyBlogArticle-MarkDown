#iPhone获取状态栏和导航栏尺寸（宽度和高度）
iPhone开发当中，有时需要获取状态栏和导航栏高度、宽度信息，方便布局其他控件。下面介绍一下如何获取这些信息：

// 状态栏(statusbar)

```

CGRect rectStatus = [[UIApplication sharedApplication] statusBarFrame];

NSLog(@”status width – %f”, rectStatus.size.width); // 宽度

NSLog(@”status height – %f”, rectStatus.size.height);   // 高度

```

// 导航栏（navigationbar）

```
CGRect rectNav = self.navigationController.navigationBar.frame;

NSLog(@”nav width – %f”, rectNav.size.width); // 宽度

NSLog(@”nav height – %f”, rectNav.size.height);   // 高度

```
  
打印结果如下：

```

2015-01-14 13:22:22.206 app_name[226:60b] status width – 320.000000

2015-01-14 13:22:22.209 app_name[226:60b] status height – 20.000000

2015-01-14 13:22:22.210 app_name[226:60b] nav width – 320.000000

2015-01-14 13:22:22.211 app_name[226:60b] nav height – 44.000000

```

