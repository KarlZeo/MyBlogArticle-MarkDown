#Cocoa 新的依赖管理工具：Carthage
说到 iOS 的依赖管理工具，大家一定首先想到的是 [CocoaPods](http://cocoapods.org/) ，不错，CocoaPods 确实是一个很好依赖管理工具，已然成为了 Cocoa 依赖管理的标准，丰富的支持库、文档等等，CocoaPods 相关的文章有很多，这里就不一一赘述了。

今天要介绍的是一款新的依赖管理工具，名曰 “[Carthage](https://github.com/Carthage/Carthage)”，名字有点难理解，简单方便，完全独立，不修改 XCode 项目文件或配置。

### 简介

我之前很少用 CocoaPods，很大一部分原因就是因为麻烦，仅个人感觉，需要牵扯 XCode 项目文件；而 Carthage 就很好的解决了我之前的烦恼，轻耦合，更灵活；使用 `xcodebuild` 工具来编译依赖项目成二进制 Framework，再引入到项目中去。

Carthage 是由 Swift 语言写的，只支持动态框架，只支持 iOS8+。

Carthage 的大致工作流程如下：

  1. 创建一个 `Cartfile` 文件，写好你要哪些依赖库
  2. 执行 `carthage update` 命令拉取源代码并编译为 Framework
  3. 把编译后的 `.framework` 拖到项目中去即可 （官方是这么说的，不过更好的办法是把 Carthage 编译的 Framework 路径加入到 Build Setting 中的 Framework Search Path，详情见后文）

执行 `update` 命令后，你的项目目录结构大致如下：

```
Cartfile
Cartfile.resolved
Carthage
- Build
- iOS
- Alamofire.framework
- Mac
- Alamofire.framework
- Checkouts
- Alamofire
- ...
xxx.xcodeproj
...
```


  * **Cartfile** 文件用来标注你需要哪些依赖库，对应版本或者 Git 分支 (需要提交到 Git)
  * **Cartfile.resolved** 文件用来跟踪项目当前所用的依赖版本号，为了保持多端开发一致 (需要提交到 Git)
  * **Carthage** 文件夹用来存放依赖库的源文件和编译后的文件 (不需要提交到 Git)

其实工作方式有点和 Cocoapods 大致相似，只不过 Cartfile 多了一个自动编译过程且与 Project 耦合更低，Cartfile 利用 xcode-select 命令来编译 Framework，如果你想用测试版的 Xcode 进行编译，执行下面这条命令，把 xcode-select 的路径改为另一版本 Xcode 就可以了

```
sudo xcode-select -s /Applications/Xcode-beta.app/Contents/Developer
```


其中 `Xcode-beta.app` 就是对应你的 Xcode 版本，你也可以改成其他版本的 Xcode

> 注：写完才发现，原来 Xcode -> Preferences -> Locations 中已经有切换 Command Line Tools 版本的选项… 

### 安装

推荐使用 [Homebrew](http://brew.sh/) 进行安装，简单方便，也便于维护：

```
brew install carthage
```


安装前最好先 update 一下，之前我就是因为没有 update，结果安装了老版本的 Carthage

```
brew update
```


### 使用

#### 添加 Cartfile 文件

类似于 CocoaPods 中的 `Podfile` 文件，把需要的包写进去就行了，具体可参阅[官方说明](https://github.com/Carthage/Carthage/blob/master/Documentation/Artifacts.md#cartfile)，如：

```
# 必须最低 2.3.1 版本
github "ReactiveCocoa/ReactiveCocoa" &gt;= 2.3.1

# 必须 1.x 版本
github "Mantle/Mantle" ~&gt; 1.0 # (大于或等于 1.0 ，小于 2.0)

# 必须 0.4.1 版本
github "jspahrsummers/libextobjc" == 0.4.1

# 使用最新的版本
github "jspahrsummers/xcconfigs"

# 使用一个私有项目，在 "development" 分支
git "https://enterprise.local/desktop/git-error-translations.git" "development"
```


暂只支持 GitHub 和 git 源，在执行 `carthage update` 命令后会在根目录创建一个`Cartfile.resolved` 文件，这个文件是生成后的依赖关系，不能修改。

#### 引入 Framework

在项目中引入依赖的 Framkework，只需要在对应 Target 中的 Build Setting 中的 Framework Search Path 项加入以下路径，Xcode 便会自动搜索目录下的 Framework：

```
$(SRCROOT)/Carthage/Build/iOS
```


> 如果是 OSX 项目则把末尾的 iOS 改为 Mac 

#### 在 Git 中忽略

如果不想把 Carthage 的依赖库 push 到 Git 仓库里，则修改 .gitignore 文件，增加忽略 Carthage 文件夹就行了：

> # Carthage
> 
> Carthage 

#### 可用命令

> `archive` : Archives a built framework into a zip that Carthage can use
    
> `bootstrap` : Check out and build the project’s dependencies
    
> `build` : Build the project’s dependencies
    
> `checkout` : Check out the project’s dependencies
    
> `copy-frameworks` : In a Run Script build phase, copies each framework specified by a SCRIPT\_INPUT\_FILE environment variable into the built app bundle
    
> `fetch` : Clones or fetches a Git repository ahead of time
    
> `help` : Display general or command-specific help
    
> `update` : Update and rebuild the project’s dependencies
    
> `version` : Display the current version of Carthage 



