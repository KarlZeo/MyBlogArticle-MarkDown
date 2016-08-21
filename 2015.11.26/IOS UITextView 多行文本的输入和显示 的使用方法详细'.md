#IOS UITextView 多行文本的输入和显示 的使用方法详细'

```
// UITextView的常用方法 主要用来输入和显示多行文本信息
UITextView *oneTextView = [[UITextView alloc] init];
oneTextView.frame = CGRectMake(0, 20, 320, 200); // 设置位置
oneTextView.backgroundColor = [UIColor whiteColor]; // 设置背景色
oneTextView.alpha = 1.0; // 设置透明度
oneTextView.text = @"18331000747 1096455447@qq.com lizi1020@sina.cn www.baidu.com"; // 设置文字
oneTextView.textAlignment = NSTextAlignmentCenter; // 设置字体对其方式
oneTextView.font = [UIFont boldSystemFontOfSize:25.5f]; // 设置字体大小
oneTextView.textColor = [UIColor redColor]; // 设置文字颜色
[oneTextView setEditable:YES]; // 设置时候可以编辑
oneTextView.dataDetectorTypes = UIDataDetectorTypeAll; // 显示数据类型的连接模式（如电话号码、网址、地址等）
oneTextView.keyboardType = UIKeyboardTypeDefault; // 设置弹出键盘的类型
oneTextView.returnKeyType = UIReturnKeySearch; // 设置键盘上returen键的类型
oneTextView.scrollEnabled = YES; // 当文字宽度超过UITextView的宽度时，是否允许滑动

[self.view addSubview:oneTextView]; // 添加到View上
[oneTextView release], oneTextView = nil; // 释放内存



// 几种常用的代理方法
//将要开始编辑
// - (BOOL)textViewShouldBeginEditing:(UITextView *)textView;

//将要结束编辑
// - (BOOL)textViewShouldEndEditing:(UITextView *)textView;

//开始编辑
// - (void)textViewDidBeginEditing:(UITextView *)textView;

//结束编辑
// - (void)textViewDidEndEditing:(UITextView *)textView;

//内容将要发生改变编辑
// - (BOOL)textView:(UITextView *)textView shouldChangeTextInRange:(NSRange)range replacementText:(NSString *)text;

//内容发生改变编辑
// - (void)textViewDidChange:(UITextView *)textView;

//焦点发生改变
// - (void)textViewDidChangeSelection:(UITextView *)textView;
```




