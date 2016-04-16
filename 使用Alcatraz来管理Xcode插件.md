# 使用Alcatraz来管理Xcode插件

## 简介

Alcatraz 是一个帮你管理 Xcode 插件、模版以及颜色配置的工具。它可以直接集成到 Xcode 的图形界面中，让你感觉就像在使用 Xcode 自带的功能一样。

## 安装和删除

使用如下的命令行来安装 Alcatraz：

```
mkdir -p ~/Library/Application\ Support/Developer/Shared/Xcode/Plug-ins; curl -L http://git.io/lOQWeA | tar xvz -C ~/Library/Application\ Support/Developer/Shared/Xcode/Plug-ins
```

如果你不想使用 Alcatraz 了，可以使用如下命令来删除：

```
rm -rf ~/Library/Application\ Support/Developer/Shared/Xcode/Plug-ins/Alcatraz.xcplugin  
rm -rf ~/Library/Application\ Support/Alcatraz
```

## 使用

安装成功后重启 Xcode，就可以在 Xcode 的顶部菜单中找到 Alcatraz，如下所示：


![](media/14606400109655/14606404320080.jpg)

点击 “Package Manager”，即可启动插件列表页面，如下所示： 

![](media/14606400109655/14606404522257.jpg)


之后你可以在右上角搜索插件，对于想安装的插件，点击其左边的图标，即可下载安装，如下所示，我正在安装`KImageNamed`插件：

![](media/14606400109655/14606404673460.jpg)


安装完成后，再次点击插件左边的图标，可以将该插件删除。

## 插件路径 {#}

Xcode 所有的插件都安装在目录`~/Library/Application Support/Developer/Shared/Xcode/Plug-ins/`下，你也可以手工切换到这个目录来删除插件。



