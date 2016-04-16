#iOS开发debug跟release版本log屏蔽方法

简单介绍以下几个宏：
  
1) `__VA_ARGS__` 是一个可变参数的宏，这个可变参数的宏是新的C99规范中新增的，目前似乎只有gcc支持（VC6.0的编译器不支持）。宏前面加上##的作用在于，当可变参数的个数为0时，这里的##起到把前面多余的","去掉,否则会编译出错。
  
2) `__FILE__` 宏在预编译时会替换成当前的源文件名
  
3) `__LINE__` 宏在预编译时会替换成当前的行号
  
4) **FUNCTION**\` 宏在预编译时会替换成当前的函数名称

  1. 在 `***-Prefix.pch` 里面添加， 重新定义系统的 `NSLog` ，`__OPTIMIZE__` 是release 默认会加的宏

```
#ifndef __OPTIMIZE__  
#define NSLog(...) NSLog(__VA_ARGS__)  
#else  
#define NSLog(...){}  
#endif  
```


2.在 `***-Prefix.pch` 里面添加 ，直接自己写 `#define` ,当 `release` 版本的时候把 `#define` 注释掉即可

```
#define IOS_DEBUG
#ifdef IOS_DEBUG  
#define NSLog(...) NSLog(__VA_ARGS__)  
#endif  
```


3.在 `***-Prefix.pch` 里面添加

```
#ifdef DEBUG    
# define DLog(format, ...) NSLog((@"[文件名:%s]" "[函数名:%s]" "[行号:%d]" format), __FILE__, __FUNCTION__, __LINE__, ##__VA_ARGS__);    
#else    
# define DLog(...);    
#endif    
```


这种方式需要修改项目的配置，使得在debug编译的时候，编译DLog的宏，产生详细的日志信息，而release的时候，不产生任何控制台输出
  
相比而言，还是第一种比较方便

转自CSDN Blog,[原文链接](http://blog.csdn.net/lvmaker/article/details/43450729).



