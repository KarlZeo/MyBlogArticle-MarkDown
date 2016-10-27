# 让从 dmg 镜像中手动安装的 xocde 跟随 mac App Store 更新

关于 macOS 我就不吐槽了,苹果把大量的 `terminal` 工具封装在 xcode 里面了.不得不说,这很鸡贼.....然而我大清朝的网络,俩字,呵呵....于是就有了各种xcode网盘下载....然后就出现了传说中的 `xcodeghost` .于是,xcode下载的问题就成了一个问题.

其实,对比一下从App Store下载的程序和手动安装的.会发现,从App Store下载的程序里面多了一个 `_MASReceipt` 文件夹.这就是关键.

找个网络好的环境先从App Store下载一遍xcode,然后备份 `_MASReceipt` 文件夹.再提前从开发者中心下载一个XCode的xip镜像扔到移动硬盘里面.等哪天重装系统,直接把xcode仍进去,然后把 `_MASReceipt` 文件夹拷贝到XCode里面,再打开App Store,看看已购项目的xcode已经从download变成open了.于是,节省了大把的时间.于是,fuck apple's network.

