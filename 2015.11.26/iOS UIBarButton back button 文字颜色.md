# iOS UIBarButton back button 文字颜色
系统默认的颜色是蓝色,蓝色不难看,但是在某些底色比较重的背景上面,蓝色就很难分辨了.更改方法很简单,在`AppDelegate.m`这个文件的

```
- (BOOL)application:(UIApplication *)application didFinishLaunchingWithOptions:
(NSDictionary *)launchOptions
```


方法里面,加入一句话就可以搞定.

```
[[UINavigationBar appearance] setTintColor:[UIColor whiteColor]];
```


**OK**

**Enjoy it!**



