#[转]Xcode7 添加PCH文件'

1.) 打开你的Xcode工程. 在Supporting Files目录下,选择 File > New > File > iOS > Other > PCH File 然后点击下一步； 
  
2.) 给你的PCH文件起名字TestDemo-Prefix.pch. 例如你的项目工程名为TestDemo然而你的PCH 文件的名字应该为 TestDemo-Prefix.pch,然后创建；

![14602742798754](https://lh3.googleusercontent.com/-Czf8LsdKRPg/V4t6Hs8tu6I/AAAAAAAAAw4/qad-VQrqo48/I/14602742798754.jpg)


3.) 选择 PCH 文件(文章的示例文件为 TestDemo-Prefix.pch) ,可以看到里面的内容如下:
  
![14602743121672](https://lh3.googleusercontent.com/-zquVDQclfZE/V4t6H0NHzXI/AAAAAAAAAw8/rG7-fKXCNac/I/14602743121672.jpg)


4.) 找到 Project > Build Settings > 搜索 “Prefix Header“； 
  
5.) “Apple LLVM 7.0 -Language″ 栏目中你将会看到 Prefix Header 关键字；
  
6.) 输入: 你的 pch 文件的绝对路径；
  
7.)，将Precompile Prefix Header为YES，预编译后的pch文件会被缓存起来，可以提高编译速度。效果如下

![14602743840031](https://lh3.googleusercontent.com/-4xb-ePxxo4M/V4t6IEVYrhI/AAAAAAAAAxA/20EFCh0Ty3k/I/14602743840031.jpg)


8.) Clean 并且 build 你的项目.
  
就是这样！Done！现在你可以使用你的 PCH 文件就像你使用老版本的Xcode一样了

转自简书,细节稍作修改,[原文链接](http://www.jianshu.com/p/e6e0e3bbbf38).

