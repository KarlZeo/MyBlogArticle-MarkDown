# 解决 xcode 各种编译错误

## "std::ios_base::Init::~Init()", referenced from

解决方案: 如果出现这样的编译问题，是需要再加进libstdc++.dylib和libstdc++.6.dylib(为6.1使用)

## apple Mach-o Linker error

解决方案: 通常是因为compile source中有相同的.m文件 
 
## 如果在真机中进行测试时出现failed to get the task for process，

解决方案: 有可能是证书出了问题。
 
## 如果出现expect a type的错误。

解决方案: 可能出现了在.h文件中的循环引用

## 这样会报linker command failed with exit code 1 (use -vto see invocation)这个错误。

解决方案: 以后不能同时有两个一样的.m文件在编译


