# [转] copy,assign,strong,retain,weak,readonly,readwrite，nonatomic，atomic，unsafe_unretained的使用与区别
最近在学习iOS的过程个遇到了不少问题，知道概念也看过示例代码，但是就是写不出来或者不知道怎么去用。
一种遇到最多的时候就是在申明一个属性的时候，比如：

```
@property （？， ？） ？ ＊！；
。。。。。。。。。
。。。。。。
。。。
。
```

对，就是这里，每次碰到这里的时候，就不知道怎么下手了，虽然看起来很简单（不过也确实是很简单），但是很容易弄混淆。
那么今天我就给大家总结一下，也作为自己以后的一个备忘录，方便以后的查阅！
 注：这几个词非常重要，是以99%以上的公司面试或者笔试必问的，所以你懂的！
 
`copy`,`assign`,`strong`,`etain`,`weak`,`readonly`,`nonatomic`的区别，有需要的朋友可以参考下。
 
这篇文章主要是从这几个词的含义和简单的使用，然后就是iOS开发中使用的时候的一些区别，这里对面试非常重要！

## 含义
### copy	
复制内容（深复制），如果调用copy的是数组，则为指针复制（浅复制），仅仅复制子元素的指针。

```
@property  (nonatomic,copy)NSString  *title;
 @property (nonatomic, copy) NSMutableArray *myArray;//not recommended
 @property (nonatomic, copy) SomeBlockType someBlock;
```
 
### assign
对基础数据类型(NSInteger，CGFloat)和C数据类型（int,  float, double, char等）

``` @property  (nonatomic, assign) int n;
 @property (nonatomic, assign) BOOL isOK;
 @property (nonatomic,  assign)  CGFloat scalarFloat;
 @property (nonatomic,  assign)  CGPoint scalarStruct;
```
 
### strong
相当于retain。Strong在ARC环境为默认属性类型。
 
```
@property  (nonatomic,readwrite,strong)NSString *title;

@property (strong, nonatomic) UIViewController *viewController;
    
@property (nonatomic,  strong) id  childObject;
```
 
### retain
NSObject及其子类。 Release旧值，retain新值。 Retain是指针复制（浅复制），引用计数加1，而不会导致内容被复制。

```
 @property  (nonatomic, retain)UIColor *myColor;
```
 
### weak
取代之前的assign，对象销毁之后会自动置为nil，防止野指针。Assign不能自动置为nil，需要手动置为nil。Delegate基本总是使用weak，以防止循环引用。特殊情况是，希望在dealloc中调用delegate的某些方法进行释放，此时如果使用weak将引起异常，因为此时已经是nil了，那么采用assign更为合适。
 

```
@property  (weak, nonatomic) IBOutlet UIButton *myButton;//处于最顶层的IBOutlet
```


应该为strong

```
 @property (nonatomic,  weak) id  parentObject;
 @property(nonatomic,readwrite,weak) id  <MyDelegate> delegate;
 @property (nonatomic,  weak) NSObject  <SomeDelegate> *delegate;
```

### readonly
此标记说明属性是只读的，默认的标记是读写，如果你指定了只读，在`@implementation`中只需要一个读取器。或者如果你使用`@synthesize`关键字，也是有读取器方法被解析。而且如果你试图使用点操作符为属性赋值，你将得到一个编译错误。
 
### readwrite
此标记说明属性会被当成读写的，这也是默认属性。设置器和读取器都需要在`@implementation`中实现。如果使用`@synthesize`关键字，读取器和设置器都会被解析。

### unsafe_unretained
`unretained`且`unsafe`，由于是`unretained`所以与`weak`有点类似，但是它是`unsafe`的.

```
 @property(nonatomic,unsafe_unretained)Book *book1;

unsafe_unretained id safeSelf = self;
```

## 这里提几个非常个重要的概念：
#### ARC－自动医用技术
ARC不是垃圾回收，而是编译器自动插入代码来减少程序员的代码输入和失误。     同时比垃圾和效率要高，因为其不影响运行时间，相当于自己管理内存。
 总是通过属性来管理实例变量（init/dealloc除外)，在dealloc中释放所有属性。 dealloc中会自动加入释放实例变量的代码，因此不必要手段增加释放实例变量的代码。不需要手动调用[super  dealloc]
 不要调用retain,release,autorelease,编译器会自动插入相关代码。 注意命名方式，不要以copyXXX方式命名不想进行retain的方法，编译器会根据方法名自动retain。   C语言结构体中不要有对象指针   id和void*只能通过桥接转换来进行转换   不要使用NSAutoreleasePool,而是使用@autoreleasepool{}代码块。 转换ARC代码：Edit->Refactor->Convert  to Objective-C ARC
retain cycle
#### 循环保留
delegate和block是产生retain  cycle的主要原因  
#### dealloc
移除观察者observers     注销通知notification     设置非weak的delegate为nil    取消timer
    
## 使用区别：
 
### 一：copy与retain：
 
1、copy其实是建立了一个相同的对象，而retain不是；
2、copy是内容拷贝，retain是指针拷贝；
3、copy是内容的拷贝 ,对于像NSString,的确是这样，但是如果copy的是一个NSArray呢?这时只是copy了指向array中相对应元素的指针.这便是所谓的"浅复制".
4、copy的情况：NSString *newPt = [pt copy];
此时会在堆上重新开辟一段内存存放@"abc" 比如0X1122 内容为@"abc 同时会在栈上为newPt分配空间 比如地址：0Xaacc 内容为0X1122 因此retainCount增加1供newPt来管理0X1122这段内存；

### 二：assign与retain：

1、assign: 简单赋值，不更改索引计数；
2、assign的情况：NSString *newPt = [pt assing];
此时newPt和pt完全相同 地址都是0Xaaaa 内容为0X1111 即newPt只是pt的别名，对任何一个操作就等于对另一个操作， 因此retainCount不需要增加；
3、assign就是直接赋值；
4、retain使用了引用计数，retain引起引用计数加1, release引起引用计数减1，当引用计数为0时，dealloc函数被调用，内存被回收；
5、retain的情况：NSString *newPt = [pt retain];
此时newPt的地址不再为0Xaaaa，可能为0Xaabb 但是内容依然为0X1111。 因此newPt 和 pt 都可以管理"abc"所在的内存，因此 retainCount需要增加1；
 
### 三：readonly：
 
readonly：只产生简单的getter,没有setter。

### 四：readwrite：
 
readwrite：同时产生setter\getter方法
 
### 五: nonatomic，atomic：

：1、非原子性访问，对属性赋值的时候不加锁，多线程并发访问会提高性能。如果不加此属性，则默认是两个访问方法都为原子型事务访问；
weak and strong property (强引用和弱引用的区别)：
：2，置成员变量的@property属性时，默认为atomic，提供多线程安全。                 在多线程环境下，原子操作是必要的，否则有可能引起错误的结果
	◦	atomic的意思就是setter/getter这个函数，是一个原语操作。如果有多个线程同时调用setter的话，不会出现某一个线程执行完setter全部语句之前，另一个线程开始执行setter情况，相当于函数头尾加了锁一样，可以保证数据的完整性。nonatomic不保证setter/getter的原语行，所以你可能会取到不完整的东西。因此，在多线程的环境下原子操作是非常必要的，否则有可能会引起错误的结果。 
	◦	比如setter函数里面改变两个成员变量，如果你用nonatomic的话，getter可能会取到只更改了其中一个变量时候的状态，这样取到的东西会有问题，就是不完整的。当然如果不需要多线程支持的话，用nonatomic就够了，因为不涉及到线程锁的操作，所以它执行率相对快些。 
 
### 六：weak 和 strong
 
	1.weak 和 strong 属性只有在你打开ARC时才会被要求使用，这时你是不能使用retain release autorelease 操作的，因为ARC会自动为你做好这些操作，但是你需要在对象属性上使用weak 和strong,其中strong就相当于retain属性，而weak相当于assign。
	2.只有一种情况你需要使用weak（默认是strong），就是为了避免retain cycles（就是父类中含有子类{父类retain了子类}，子类中又调用了父类{子类又retain了父类}，这样都无法release）
	3.声明为weak的指针，指针指向的地址一旦被释放，这些指针都将被赋值为nil。这样的好处能有效的防止野指针。
 
### 七：ARC(Automatic Reference Counting):

1、就是代码中自动加入了retain/release，原先需要手动添加的用来处理内存管理的引用计数的代码可以自动地由编译器完成了。
该机能在 iOS 5/ Mac OS X 10.7 开始导入，利用 Xcode4.2 以后可以使用该特性。
 
### 八：strong,weak,copy 具体用法：

1.具体一点：IBOutlet可以为weak，NSString为copy，Delegate一般为weak，其他的看情况。一般来说，类 “内部”的属性设置为strong，类“外部”的属性设置为weak。说到底就是一个归属权的问题。小心出现循环引用导致内存无法释放。
2.不用ARC的话就会看到很多retian。
3.如果你写了@synthesize abc = _abc；的话，系统自动帮你声明了一个_abc的实例变量。
使用assign: 对基础数据类型 （NSInteger）和C数据类型（int, float, double, char,等）
使用copy： 对NSString
使用retain： 对其他NSObject和其子类
 
### 注意：

assign：默认类型,setter方法直接赋值，而不进行retain操作
retain：setter方法对参数进行release旧值，再retain新值。
copy：setter方法进行Copy操作，与retain一样


