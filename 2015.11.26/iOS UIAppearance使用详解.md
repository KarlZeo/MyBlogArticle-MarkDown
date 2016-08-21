#iOS UIAppearance使用详解

iOS5及其以后提供了一个比较强大的工具UIAppearance，我们通过UIAppearance设置一些UI的全局效果，这样就可以很方便的实现UI的自定义效果又能最简单的实现统一界面风格，它提供如下两个方法。

```
+(instancetype)appearance
```


这个方法是统一全部改，比如你设置UINavBar的tintColor，你可以这样写：`[[UINavigationBar appearance] setTintColor:myColor];`

```
+ (instancetype)appearanceWhenContainedIn:(Class &lt;&gt;)ContainerClass,...
```


这个方法可设置某个类的改变：例如：设置UIBarButtonItem 在UINavigationBar、UIPopoverController、UITabbar中的效果。就可以这样写

```
[[UIBarButtonItem appearanceWhenContainedIn:[UINavigationBar class], [UIPopoverController class],[UITabbar class] nil] setTintColor:myPopoverNavBarColor];
```


请注意＊使用appearance设置UI效果最好采用全局的设置，在所有界面初始化前开始设置，否则可能失效。
  
具体UI外观修改如下：

## 1.修改导航栏背景 {#toc_0}

代码如下：

```
UINavigationBar * appearance = [UINavigationBar appearance];
UIImage *navBackgroundImg =[UIImage imageNamed:@"navBg.png”];
[appearance setBackgroundImage:navBackgroundImg forBarMetrics:UIBarMetricsDefault];
```


## 2.标签栏（UITabbar） {#toc_1}

代码如下：

```
UITabBar *appearance = [UITabBar appearance];
//设置背景图片
[appearance setBackgroundImage:[UIImage imageNamed:@"tabbar_bg.png"]];
//门置选择item的背景图片
UIImage * selectionIndicatorImage =[[UIImage imageNamed:@"tabbar_slider"]resizableImageWithCapInsets:UIEdgeInsetsMake(4, 0, 0, 0)] ;
[appearance setSelectionIndicatorImage:selectionIndicatorImage];
```


## 3.分段控件（UISegmentControl） {#toc_2}

代码如下：

```
UISegmentedControl *appearance = [UISegmentedControl appearance];
//Segmenteg正常背景
[appearance setBackgroundImage:[UIImage imageNamed:@"Segmente.png"]
forState:UIControlStateNormal
barMetrics:UIBarMetricsDefault];
//Segmente选中背景
[appearance setBackgroundImage:[UIImage imageNamed:@"Segmente_a.png"]
forState:UIControlStateSelected
barMetrics:UIBarMetricsDefault];
//Segmente左右都未选中时的分割线
//BarMetrics表示navigation bar的状态，UIBarMetricsDefault 表示portrait状态（44pixel height），UIBarMetricsLandscapePhone 表示landscape状态（32pixel height）
[appearance setDividerImage:[UIImage imageNamed:@"Segmente_line.png"]
forLeftSegmentState:UIControlStateNormal
rightSegmentState:UIControlStateNormal
barMetrics:UIBarMetricsDefault];
[appearance setDividerImage:[UIImage imageNamed:@"Segmente_line.png"]
forLeftSegmentState:UIControlStateSelected
rightSegmentState:UIControlStateNormal
barMetrics:UIBarMetricsDefault];
[appearance setDividerImage:[UIImage imageNamed:@"Segmente_line.png"]
forLeftSegmentState:UIControlStateNormal
rightSegmentState:UIControlStateSelected
barMetrics:UIBarMetricsDefault];
//字体
NSDictionary *textAttributes1 = @{UITextAttributeFont: [UIFont systemFontOfSize:18],
UITextAttributeTextColor: [UIColor blueColor],
UITextAttributeTextShadowColor: [UIColor whiteColor],
UITextAttributeTextShadowOffset: [NSValue valueWithCGSize:CGSizeMake(1, 1)]};
[appearance setTitleTextAttributes:textAttributes1 forState:1];
NSDictionary *textAttributes2 = @{UITextAttributeFont: [UIFont systemFontOfSize:18],
UITextAttributeTextColor: [UIColor whiteColor],
UITextAttributeTextShadowColor: [UIColor blackColor],
UITextAttributeTextShadowOffset: [NSValue valueWithCGSize:CGSizeMake(1, 1)]};
[appearance setTitleTextAttributes:textAttributes2 forState:0];
```


## 4.UIBarbutton {#toc_3}

注意：UIBarbutton有leftBarButton，rightBarButton和backBarButton，其中backBarButton由于带有箭头，需要单独设置。
  
barButton背景设置是ios6.0及以后的，而backbutton是ios5.0及以后的，这里要注意！
  
代码如下：

```
//修改导航条上的UIBarButtonItem
UIBarButtonItem *appearance = [UIBarButtonItem appearanceWhenContainedIn:[UINavigationBar class], nil];
//设置导航栏的字体包括backBarButton和leftBarButton，rightBarButton的字体
NSDictionary *textAttributes = @{UITextAttributeFont: [UIFont systemFontOfSize:18],
UITextAttributeTextColor: [UIColor blueColor],
UITextAttributeTextShadowColor: [UIColor whiteColor],
UITextAttributeTextShadowOffset: [NSValue valueWithCGSize:CGSizeMake(1, 1)]};
[appearance setTitleTextAttributes:textAttributes forState:1];//forState为0时为下正常状态，为1时为点击状态。
//修改leftBarButton，rightBarButton背景效果
[appearance setBackgroundImage:[UIImage imageNamed:@"navBarButton.png"]
forState:UIControlStateNormal
style:UIBarButtonItemStyleBordered
barMetrics:UIBarMetricsDefault];
[appearance setBackgroundImage:[UIImage imageNamed:@"navBarButton_a.png"]
forState:UIControlStateHighlighted
style:UIBarButtonItemStyleBordered
barMetrics:UIBarMetricsDefault];
//backBarButton需要单独设置背景效果。只能在ios6.0以后才能用
[appearance setBackButtonBackgroundImage:[UIImage imageNamed:@"nav_bg.png"]
forState:0
barMetrics:UIBarMetricsDefault];
[appearance setBackButtonBackgroundImage:[UIImage imageNamed:@"work.png"]
forState:1
barMetrics:UIBarMetricsDefault];
[appearance setBackButtonTitlePositionAdjustment:UIOffsetMake(2, -1)
forBarMetrics:UIBarMetricsDefault];
```


## 5.工具栏（UIToolbar） {#toc_4}

```
UIToolbar *appearance = [UIToolbar appearance];
//样式和背景二选一即可，看需求了
//样式（黑色半透明，不透明等）设置
[appearance setBarStyle:UIBarStyleBlackTranslucent];
//背景设置
[appearance setBackgroundImage:[UIImage imageNamed:@"toolbarBg.png"]
forToolbarPosition:UIToolbarPositionAny
barMetrics:UIBarMetricsDefault];
```




