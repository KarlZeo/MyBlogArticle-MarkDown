---
id: 171
title: iOS开发UI篇—iOS开发中三种简单的动画设置
date: 2016-02-19T22:41:34+08:00
author: Kanaan Austen
layout: post
guid: https://blog.nieyujiang.info/?p=171
permalink: /2016/02/19/ios-development-ui-ios-development-in-three-simple-animation-settings/
dsq_thread_id:
  - 4651687605
views:
  - 7
categories:
  - iOS 编程
---
&nbsp;
  
**iOS开发UI篇—iOS开发中三种简单的动画设置**

【在ios开发中，动画是廉价的】

**一、首尾式动画**

代码示例：

// beginAnimations表示此后的代码要“参与到”动画中 [UIView beginAnimations:nil context:nil]; //设置动画时长 [UIView setAnimationDuration:2.0]; self.headImageView.bounds = rect; // commitAnimations,将beginAnimation之后的所有动画提交并生成动画 [UIView commitAnimations];

说明：如果只是修改控件的属性，使用首尾式动画还是比较方便的，但是如果需要在动画完成后做后续处理，就不是那么方便了

二、block代码块动画

代码示例：

//简单的动画效果 [UIView animateWithDuration:2.0 animations:^{ showlab.alpha=0; } completion:^(BOOL finished) { [showlab removeFromSuperview]; }];

说明：

（1）在实际的开发中更常用的时block代码块来处理动画操作。

（2）块动画相对来说比较灵活，尤为重要的是能够将动画相关的代码编写在一起，便于代码的阅读和理解.

三、序列帧动画（以一个简单的TOM猫动画示例）

![](https://i1.wp.com/blog.nieyujiang.info/wp-content/uploads/2015/12/7d928e58daccf252e1a1bb5ea0baf8b8.png?resize=743%2C379)

导入提前准备好的素材，对UIImageview和button按钮进行连线。

代码示例：

  * (IBAction)eat { NSMutableArray _arrayM=[NSMutableArray array]; for (int i=0; i<40; i++) { [arrayM addObject:[UIImage imageNamed:[NSString stringWithFormat:@&#8221;eat_%02d.jpg&#8221;,i]]]; } //设置动画数组 [self.tom setAnimationImages:arrayM]; //设置动画播放次数 [self.tom setAnimationRepeatCount:1]; //设置动画播放时间 [self.tom setAnimationDuration:40_0.075]; //开始动画 [self.tom startAnimating]; }

点击按钮，即可执行动画，实现效果截图如下：

![](https://i0.wp.com/blog.nieyujiang.info/wp-content/uploads/2015/12/ae20bfac4b02c22b9dc3ae27624a0ae8.png?resize=248%2C372)

四、补充知识

  1. Images.xcassets中的素材

（1）只支持png格式的图片

（2） 图片只支持[UIImage imageNamed]的方式实例化，但是不能从Bundle中加载

（3）  在编译时，Images.xcassets中的所有文件会被打包为Assets.car的文件

&nbsp;

  1. UIImageView的序列帧动画（需要考虑程序性能，释放数据）

// 0. 是否正在动画

[self.tom isAnimating];

// 1. 设置图片的数组

[self.tom setAnimationImages:arrayM];

// 2. 设置动画时长，默认每秒播放30张图片

[self.tom setAnimationDuration:arrayM.count * 0.075];

// 3. 设置动画重复次数，默认为0，无限循环

[self.tom setAnimationRepeatCount:1];

// 4. 开始动画

[self.tom startAnimating];

// 5. 动画播放完成后，清空动画数组

[self.tom performSelector:@selector(setAnimationImages:) withObject:nilafterDelay:self.tom.animationDuration];

&nbsp;

  1. UIImage imageNamed

（1）在图片使用完成后，不会直接被释放掉，具体释放时间由系统决定，适用于图片小，常用的图像处理

（2）如果要释放快速释放图片，可以使用[UIImage imageWithContentsOfFile:path]实例化图像

&nbsp;

  1. 方法重构的策略

（1） 将具有共性的代码复制到一个新的方法

（2）根据不同的调用情况，增加方法的参数

提示：在写程序时不要着急重构，有时候把代码先写出来，更容易看清楚如何重构才会更好

&nbsp;

  1. Bundle（包）中的图片素材

往项目中拖拽素材时，通常选择

（1） Destination: 勾选

（2） Folders:

1)选择第一项：黄色文件夹

注意点：Xcode中分文件夹，Bundle中所有所在都在同一个文件夹下，因此，不能出现文件重名的情况

特点：

a.可以直接使用[NSBundle mainBundle]作为资源路径，效率高！

b.可以使用[UIImage imageNamed:]加载图像

2)选择第二项：蓝色文件夹

注意点：Xcode中分文件夹，Bundle中同样分文件夹，因此，可以出现文件重名的情况

特点：

a.需要在[NSBundle mainBundle]的基础上拼接实际的路径，效率较差

b.不能使用[UIImage imageNamed:]加载图

&nbsp;