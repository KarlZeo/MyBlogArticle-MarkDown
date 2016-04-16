#用 Sublime Text 3 构建简易的 Java 开发环境

## 1. 安装 Java 环境和 Jdk {#toc_0}

从官网下载相应的 DMG 镜像文件即可,挂载安装.

## 2. 安装 Sublime Text 3 {#toc_1}

从官网下载相应的 DMG 镜像文件即可,挂载安装.然后激活.

## 3. 配置 Sublime Text 3 的编译系统 {#toc_2}

选择 `Tool` > `Build System` > `New Build System` .
  
将弹出的页面里面所有的东西全部删除,粘贴以下代码.

```
{
    "shell_cmd": "javac -encoding utf-8 $file_name && java $file_base_name",
    "file_regex": "^ *\\[javac\\] (.+):([0-9]+):() (.*)$",
    "selector": "source.java",    
    "encoding": "utf-8"
}
```


## 4. 保存,打完收工. {#toc_3}

记得保存!
  
记得保存!
  
记得保存!
  
重要的事情说三遍.不说了,累了.



