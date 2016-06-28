# 用 Sublime Text 3 搭建简易的 PHP 开发环境 
添加 PHP 的 build system, Tools->Build System-> New Build System ,默认配置文件张下面这个样子.

```
{
    "cmd": ["make"]
}
```

修改一下下,变成下面这个样子:

```
{ 
    "cmd": ["php", "$file"],
    "file_regex": "php$", 
    "selector": "source.php" 
}
```
保存在默认的目录下,命名为 `php.sublime-build `.



