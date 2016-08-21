# 解决 Xcode'cannot create _weak reference in file using manual reference counting'错误
更新 Xcode7.3 以后,使用 `MJExtension`框架的时候,出现了一个 `cannot create _weak reference in file using manual reference counting` 的错误.谷歌了一下,发现在 Xcode 工程里面改一个设置即可.
### 解决方案

1. 打开工程设置的 `Build Settings`
2. 选择 `Apple LLVM 7.1 - Language - Objective C`
3. 更改 `Weak References in Manual Retain Release` 选项为 `Yes`

搞定.重新编译一下,错误消失.



