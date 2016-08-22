# Aria2 配置及使用详细教程
#### 一、安装 Aria2

没啥好说的,直接 brew 就行.

```
brew install aria2
```


#### 二、配置

从网上找一个配置文件.我的是从`YAAW`的示例配置抄的.[点我打开 YAAW地址](http://aria2c.com/usage.html)

```
## '#'开头为注释内容, 选项都有相应的注释说明, 根据需要修改 ##
## 被注释的选项填写的是默认值, 建议在需要修改时再取消注释 ##

## 文件保存相关 ##

# 文件的保存路径(可使用绝对路径或相对路径), 默认: 当前启动位置
dir=~/downloads
# 启用磁盘缓存, 0为禁用缓存, 需1.16以上版本, 默认:16M
#disk-cache=32M
# 文件预分配方式, 能有效降低磁盘碎片, 默认:prealloc
# 预分配所需时间: none &lt; falloc ? trunc &lt; prealloc
# falloc和trunc则需要文件系统和内核支持
# NTFS建议使用falloc, EXT3/4建议trunc, MAC 下需要注释此项
file-allocation=none
# 断点续传
continue=true

## 下载连接相关 ##

# 最大同时下载任务数, 运行时可修改, 默认:5
max-concurrent-downloads=1
# 同一服务器连接数, 添加时可指定, 默认:1
max-connection-per-server=5
# 最小文件分片大小, 添加时可指定, 取值范围1M -1024M, 默认:20M
# 假定size=10M, 文件为20MiB 则使用两个来源下载; 文件为15MiB 则使用一个来源下载
min-split-size=10M
# 单个任务最大线程数, 添加时可指定, 默认:5
split=5
# 整体下载速度限制, 运行时可修改, 默认:0
#max-overall-download-limit=0
# 单个任务下载速度限制, 默认:0
#max-download-limit=0
# 整体上传速度限制, 运行时可修改, 默认:0
#max-overall-upload-limit=0
# 单个任务上传速度限制, 默认:0
#max-upload-limit=0
# 禁用IPv6, 默认:false
disable-ipv6=true

## 进度保存相关 ##

# 从会话文件中读取下载任务
input-file=~/.aria2/aria2.session
# 在Aria2退出时保存`错误/未完成`的下载任务到会话文件
save-session=~/.aria2/aria2.session
# 定时保存会话, 0为退出时才保存, 需1.16.1以上版本, 默认:0
#save-session-interval=60

## RPC相关设置 ##

# 启用RPC, 默认:false
enable-rpc=true
# 允许所有来源, 默认:false
rpc-allow-origin-all=true
# 允许非外部访问, 默认:false
rpc-listen-all=true
# 事件轮询方式, 取值:[epoll, kqueue, port, poll, select], 不同系统默认值不同
#event-poll=select
# RPC监听端口, 端口被占用时可以修改, 默认:6800
#rpc-listen-port=6800
# 设置的RPC授权令牌, v1.18.4新增功能, 取代 --rpc-user 和 --rpc-passwd 选项
#rpc-secret=&lt;TOKEN&gt;
# 设置的RPC访问用户名, 此选项新版已废弃, 建议改用 --rpc-secret 选项
#rpc-user=&lt;USER&gt;
# 设置的RPC访问密码, 此选项新版已废弃, 建议改用 --rpc-secret 选项
#rpc-passwd=&lt;PASSWD&gt;

## BT/PT下载相关 ##

# 当下载的是一个种子(以.torrent结尾)时, 自动开始BT任务, 默认:true
#follow-torrent=true
# BT监听端口, 当端口被屏蔽时使用, 默认:6881-6999
listen-port=51413
# 单个种子最大连接数, 默认:55
#bt-max-peers=55
# 打开DHT功能, PT需要禁用, 默认:true
enable-dht=false
# 打开IPv6 DHT功能, PT需要禁用
#enable-dht6=false
# DHT网络监听端口, 默认:6881-6999
#dht-listen-port=6881-6999
# 本地节点查找, PT需要禁用, 默认:false
#bt-enable-lpd=false
# 种子交换, PT需要禁用, 默认:true
enable-peer-exchange=false
# 每个种子限速, 对少种的PT很有用, 默认:50K
#bt-request-peer-speed-limit=50K
# 客户端伪装, PT需要
peer-id-prefix=-TR2770-
user-agent=Transmission/2.77
# 当种子的分享率达到这个数时, 自动停止做种, 0为一直做种, 默认:1.0
seed-ratio=0
# 强制保存会话, 即使任务已经完成, 默认:false
# 较新的版本开启后会在任务完成后依然保留.aria2文件
#force-save=false
# BT校验相关, 默认:true
#bt-hash-check-seed=true
# 继续之前的BT任务时, 无需再次校验, 默认:false
bt-seed-unverified=true
# 保存磁力链接元数据为种子文件(.torrent文件), 默认:false
bt-save-metadata=true
```


在你的用户根目录下创建一个文件夹,名为`.aria2`
  
把这些东西复制到你的电脑,存到本地,保存为 `aria.conf`的文件放在你的电脑的`.aria2`文件夹中.
  
在`.aria2`文件夹中输入`touch aria2.session`创建一个`aria2.session`文件.

在终端输入`aria2c`,查看是否可以运行.

#### 三、安装前端

Aria 2 虽然是一个基于命令行的下载工具，但仍有好心大神开发了更直观的 UI 方便使用，常用的如下：

最常用的[webui-aria2](http://ziahamza.github.io/webui-aria2/)

也可以用binux大神的[YAAW](http://binux.github.io/yaaw/demo/)

如果你很厉害，也可以去 https://github.com/ziahamza/webui-aria2 或 https://github.com/binux/yaaw 下载所需文件自己搭建server

本教程以 webui-aria2 为参考，请继续阅读。

完成了上述的几个步骤之后就可以进入 UI 界面操作，操作地址：http://ziahamza.github.io/webui-aria2/

#### 四、使用方法(默认使用 chrome)

安装 chrome 插件.

BaiduExporter(百度云下载地址到处插件)[点我下载](https://chrome.google.com/webstore/detail/baiduexporter/mjaenbjdjmgolhoafkohbhhbaiedbkno)

```
BaiduExporter 配置及使用

配置
打开BaiduExporter设置,将User-agent设置为 : netdisk;5.2.7;PC;PC-Windows;6.2.9200;WindowsBaiduYunGuanJia
referer 设置为：http://pan.baidu.com/disk/home

使用
打开百度云盘,找到你想要下载的文件,勾选,然后选择上面的导出到 aria 2选项即可.
```


迅雷离线助手(迅雷下载地址到处插件)[点我下载](https://chrome.google.com/webstore/detail/thunderlixianassistant/eehlmkfpnagoieibahhcghphdbjcdmen?hl=zh-CN)

```
迅雷离线助手 配置及使用
基本与 百度云盘 的方式一样
```


设置Aria2 JSON-RPC Path

```
http://localhost:6800/jsonrpc
```




