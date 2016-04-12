---
id: 209
title: iOS打电话、发短信、发邮件功能开发
date: 2016-02-19T22:54:14+08:00
author: Kanaan Austen
layout: post
guid: https://blog.nieyujiang.info/?p=209
permalink: /2016/02/19/development-of-ios-make-phone-calls-send-text-messages-e-mail/
dsq_thread_id:
  - 4636608452
views:
  - 19
categories:
  - OC
---
<!--wp-compress-html-->

<!--wp-compress-html no compression-->

#1.发短信
  
实现打电话的功能，主要二种方法，下面我就分别说说它们的优缺点。

##1.1.发短信(1)——URL
  
// 直接拨号，拨号完成后会停留在通话记录中

###1、方法：
  
NSURL *url = [NSURL URLWithString:@&#8221;sms://10010&#8243;];

[[UIApplication sharedApplication] openURL:url];

###2、优点：
  
–简单
  
###3、缺点：
  
–不能指定短信内容，而且不能自动回到原应用

##1.2发短信(2)——MessageUI框架
  
如果自定义短信，需要使用一个框架MessageUI。

###优点

  1. 从应用出去能回来</p> 
  2. 可以多人

  3. 可以自定义消息，消息支持HTML格式的

而且如果在苹果系统中，如果彼此的手机都是iOS设备，并且开通了iMessage功能，彼此之间的短信

是走网络通道，而不走运营商的通道！

<pre class="prettyprint" ><code>- (void)msg2
{
// 判断用户设备能否发送短信
if (![MFMessageComposeViewController canSendText]) {
return;
}

// 1. 实例化一个控制器
MFMessageComposeViewController *controller = [[MFMessageComposeViewController alloc] init];

// 2. 设置短信内容
// 1) 收件人
controller.recipients = @[@"10010", @"10086"];

// 2) 短信内容
controller.body = @"给您拜个晚年，祝您晚年快乐！";

// 3) 设置代理
controller.messageComposeDelegate = self;

// 3. 显示短信控制器
[self presentViewController:controller animated:YES completion:nil];
}
</code></pre>

记得发完短信记得调用代理方法关闭窗口

<pre class="prettyprint" ><code>#pragma mark 短信控制器代理方法
/**
短信发送结果

MessageComposeResultCancelled, 取消
MessageComposeResultSent, 发送
MessageComposeResultFailed 失败
*/
- (void)messageComposeViewController:(MFMessageComposeViewController *)controller didFinishWithResult:(MessageComposeResult)result
{
NSLog(@"%d", result);

// 在面向对象程序开发中，有一个原则，谁申请，谁释放！
// *** 此方法也可以正常工作，因为系统会将关闭消息发送给self
// [controller dismissViewControllerAnimated:YES completion:nil];

// 应该用这个！！！
[self dismissViewControllerAnimated:YES completion:nil];
}
</code></pre>

#2.发邮件

<pre class="prettyprint" ><code>- (void)sendmail
{
// 1. 先判断能否发送邮件
if (![MFMailComposeViewController canSendMail]) {
// 提示用户设置邮箱
return;
}

// 2. 实例化邮件控制器，准备发送邮件
MFMailComposeViewController *controller = [[MFMailComposeViewController alloc] init];

// 1) 主题 xxx的工作报告
[controller setSubject:@"我的工作报告"];
// 2) 收件人
[controller setToRecipients:@[@"4800607@gmail.com"]];

// 3) cc 抄送
// 4) bcc 密送(偷偷地告诉，打个小报告)
// 5) 正文
[controller setMessageBody:@"这是我的&lt;font color=\"blue\"&gt;工作报告&lt;/font&gt;，请审阅！&lt;BR /&gt;P.S. 我的头像牛X吗？" isHTML:YES];

// 6) 附件
UIImage *image = [UIImage imageNamed:@"头像1.png"];
NSData *imageData = UIImagePNGRepresentation(image);
// 1&gt; 附件的二进制数据
// 2&gt; MIMEType 使用什么应用程序打开附件
// 3&gt; 收件人接收时看到的文件名称
// 可以添加多个附件
[controller addAttachmentData:imageData mimeType:@"image/png" fileName:@"头像.png"];

// 7) 设置代理
[controller setMailComposeDelegate:self];

// 显示控制器
[self presentViewController:controller animated:YES completion:nil];
}
</code></pre>

同样要记得发完邮件记得调用代理方法关闭窗口

<pre class="prettyprint" ><code>#pragma mark - 邮件代理方法
/**
MFMailComposeResultCancelled, 取消
MFMailComposeResultSaved, 保存邮件
MFMailComposeResultSent, 已经发送
MFMailComposeResultFailed 发送失败
*/
- (void)mailComposeController:(MFMailComposeViewController *)controller didFinishWithResult:(MFMailComposeResult)result error:(NSError *)error
{
// 根据不同状态提示用户
NSLog(@"%d", result);

[self dismissViewControllerAnimated:YES completion:nil];
}
</code></pre>

#3.打电话
  
打电话有三种方式可以实现，优缺点也各不同

##3.1.打电话不回引用

<pre class="prettyprint" ><code>1 - (void)tel1
2 {
3 // 直接拨号，拨号完成后会停留在通话记录中
4 NSURL *url = [NSURL URLWithString:@"tel://10010"];
5
6 [[UIApplication sharedApplication] openURL:url];
7 }
</code></pre>

##3.2.出去打电话然后回来

<pre class="prettyprint" ><code>- (void)tel2
{
// 但是：telprompt协议属于苹果的私有协议，一旦程序中使用了此协议，程序无法上架
// 针对越狱的机器开发的系统，可以使用此协议
NSURL *url = [NSURL URLWithString:@"telprompt://10010"];

[[UIApplication sharedApplication] openURL:url];
}
</code></pre>

##3.3借助UIWebView打电话（会回来）
  
一般都是用这种，解决了不越狱的问题。

<pre class="prettyprint" ><code>- (void)tel3
{
// 提示：不要将webView添加到self.view，如果添加会遮挡原有的视图
// 懒加载
if (_webView == nil) {
_webView = [[UIWebView alloc] init];
}
NSLog(@"%p", _webView);

// _webView = [[UIWebView alloc] initWithFrame:self.view.bounds];
// [self.view addSubview:_webView];

NSURL *url = [NSURL URLWithString:@"tel://10010"];
NSURLRequest *request = [NSURLRequest requestWithURL:url];

[_webView loadRequest:request];
}
</code></pre>

<!--wp-compress-html no compression-->

<!--wp-compress-html-->