#iOS懒加载
#### 在iOS开发摸爬打滚了许久，谈谈自己学习以及开发iOS的一些经验，文章比较随性，算是记录自己的成长吧！希望有些我走的弯路以及曾经让我捉耳挠腮的问题可以帮助读者少走一些弯路。

#### 本文来谈一谈在开发中非常实用的懒加载技术吧！

  * 所谓的懒加载可以定义为：延时加载，即当对象需要用到的时候再去加载。其实就是所谓的重写对象的get方法,当系统或者开发者调用对象的get方法时，再去加载对象。

```
需要注意：重写get方法时，先判断对象当前是否为空，为空的话再去实例化对象
```


  * 懒加载的优点 &#8211; 不需将对象的实例化写到viewDidLoad，可以简化代码，增强代码的可读性
  * 对象的实例化在getter方法中，各司其职，降低耦合性
  * 对系统的内存占用率会减小

#### viewDidLoad正常加载代码示例

  * 没用懒加载的时候，从plist获取数据，返回一个数组，需要写在viewDidLoad方法中获取

```
@interface ViewController ()

@property (nonatomic, strong) NSArray *shopData;

@end

@implementation ViewController

- (void)viewDidLoad {

[super viewDidLoad];

_shopData = [NSArray arrayWithContentsOfFile:
[[NSBundle mainBundle] pathForResource:@"shop" ofType:@"plist"]];
}

@end
```


  * 显而易见，当控制器被加载完成后就会加载当前的shopData，假如shopData是在某些事件被触发的时候才会被调用，没必要在控制器加载完就去获取plist文件，如果事件不被触发，代表着shopData永远不会被用到，这样在viewDidLoad中加载shopData就会十分多余，并且耗用内存

#### 懒加载代码示例

```
- (void)viewDidLoad {

[super viewDidLoad];
}

- (NSArray *)shopData
{
if (!_shopData) {
_shopData = [NSArray arrayWithContentsOfFile:
[[NSBundle mainBundle] pathForResource:@"shop" ofType:@"plist"]];
}
return _shopData;
}

@end
```


  * 当需要用到shopData的时候，就会调用[self shopData]的方法（即getter方法），此时系统会去调用getter方法，然后再getter方法中获取plist文件内容，然后返回使用（需要注意在getter方法里切勿使用self.shopData，因为self.shopData会调用getter方法，造成死循环）

#### 总结：懒加载即用到时方去加载对象



