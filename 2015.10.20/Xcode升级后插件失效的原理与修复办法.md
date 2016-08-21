# Xcode升级后插件失效的原理与修复办法

Xcode 的插件大大丰富了 Xcode 的功能，而且有了 [Alcatraz](https://github.com/supermarin/Alcatraz) ，插件的管理也非常容易，像我这种 Vim 党完全离不开 [XVim](https://github.com/XVimProject/XVim)。但是有个非常恼人的问题：一旦升级 Xcode ，插件就失效！

之前 Xcode 升级到6.2的时候遇到过插件失效的问题，Google 之后把一段很长命令复制到 Terminal 后运行一下即可，当时一看解决了，顿时觉得满足感爆棚，自己可以拯救地球了~就没有再深入，结果升级到6.3时又遇到了。“同样的招式对圣斗士是不能使用第二次的！”，同样的坑对有节操的程序员是不能掉进去第二次的！因此这一次一定要搞清楚为什么会这样，以后再次遇到了如何解决。

### 问题原因

Xcode 的插件放置在 `~/Library/Application\ Support/Developer/Shared/Xcode/Plug-ins` 目录下，为 .xcplugin 格式。通过 Show Content 可以看到 xcplugin 中存在一个 Info.plist，其中有一项为 **DVTPlugInCompatibilityUUIDs**，而这就是插件失效的原因。

由于 Apple 没有公开插件开发的相关资料，这里我只能通过命名跟值猜测 DVTPlugInCompatibilityUUIDs 的作用：**插件通过 DVTPlugInCompatibilityUUIDs 来指定能够运行此插件的 Xcode 版本**。因此，DVTPlugInCompatibilityUUIDs 中存放的是 Xcode 版本对应的 UUID，Xcode 在启动加载控件时，将当前 UUID 同插件 Info.plist 中 DVTPlugInCompatibilityUUIDs 存放的 UUID 数组进行匹配，如果没有匹配项，说明此插件无法在该版本的 Xcode 运行，插件也就失效了。

### 解决办法

解决办法非常简单：将当前版本的 UUID 加到 DVTPlugInCompatibilityUUIDs 中即可。但是插件比较多（1个及以上）的情况下，一个个的打开修改非常无聊跟低效，作为“懒惰”的程序员，这时候就要用上命令行，让重复劳动自动化。思路为将命令分为两部分：

  1. 通过 `find` 命令在插件目录下找到所有插件的 Info.plist 文件。
  2. 通过 `xargs` 命令对上一步的搜索结果进行“for 循环”（就这样理解吧），针对每一个 Info.plist 文件，利用 `defaults write` 命令将当前版本的 UUID 加到 DVTPlugInCompatibilityUUIDs 中。

此时问题来了，挖掘机技术。。。不对，是如何获取当前版本 Xcode 的 UUID 呢？首先关掉 Xcode，打开 Terminal，输入 `tail -f /var/log/system.log`，再次打开 Xcode，就能看到如下 log 信息：

> [MT] PluginLoading: Required plug-in compatibility UUID 9F75337B-21B4-4ADC-B558-F9CADF7073A7 for plug-in at path ‘~/Library/Application Support/Developer/Shared/Xcode/Plug-ins/Alcatraz.xcplugin’ not present in DVTPlugInCompatibilityUUIDs 

可以看到，log 信息表明 Xcode 加载插件失败的原因，并且能够看到当前版本（6.3）Xcode 的 UUID 为 `9F75337B-21B4-4ADC-B558-F9CADF7073A7`。经过 [@Kyrrr](http://weibo.com/u/2626996387) 的提醒，有一种更好的方式来获取当前版本 Xcode 的 UUID：通过 `defaults read` 命令从 Xcode 的 Info.plist 读取 DVTPlugInCompatibilityUUID。

最终的命令为：

find ~/Library/Application\ Support/Developer/Shared/Xcode/Plug-ins -name Info.plist -maxdepth 3 | xargs -I{} defaults write {} DVTPlugInCompatibilityUUIDs -array-add `defaults read /Applications/Xcode.app/Contents/Info.plist DVTPlugInCompatibilityUUID`

在 Terminal 中运行上述命令就解决了插件失效的问题，在插件 Info.plist 的 DVTPlugInCompatibilityUUIDs 中也能看到新增的 UUID 了。

