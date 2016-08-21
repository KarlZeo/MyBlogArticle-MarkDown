# OpenWRT 作死记录
## 1. 什么是OpenWRT
OpenWrt是适合于嵌入式设备的一个Linux发行版。相对原厂固件而言，OpenWrt不是一个单一、静态的固件，而是提供了一个可添加软件包的可写的文件系统。这使使用者可以自由的选择应用程序和配置，而不必受设备提供商的限制，并且可以使用一些适合某方面应用的软件包来定制你的设备。对于开发者来说，OpenWrt是一个框架，開發者不必麻烦的构建整个固件就能得到想要的应用程序；对于使用者来说，这意味着完全定制的能力，與以往不同的方式使用设备，OPKG包含超过3500个软件。 默认使用LuCI作为web交互界面。

## 2. 设备参数
*  型号 : NETGEAR WNDR3800
*  CPU : Atheros AR7161 rev 2 680MHz
*  RAM : 128MiB
*  Flash : 16MiB / generic

## 3. 怎么选择固件

### 下载最新版的OpenWRT固件

#### 1. 进入OpenWrt固件下载主页面：

	[http://downloads.openwrt.org/](http://downloads.openwrt.org/)

	Binary Releasesy就是最后的稳定发行版，如目前是
	
	```
	Chaos Calmer 15.05.1
	Released: Mon, 16 Mar 2016
	```
	
	Development Snapshots是开发版，包含最新的功能，但可能不够稳定。
	
[	http://downloads.openwrt.org/snapshots/trunk/](http://downloads.openwrt.org/snapshots/trunk/)
	
	如果使用Snapshots没有什么问题，当然是最好的选择，否则可以尝试一下稳定发行版。
	

#### 2. 选择CPU类型

	打开页面后，选择你的路由器的芯片型号进入，很多是ar71xx系列，于是进入了：
	
	[http://downloads.openwrt.org/snapshots/trunk/ar71xx/](http://downloads.openwrt.org/snapshots/trunk/ar71xx/)

#### 3. 选择 Flash类型

	再选择Flash类型，比如WNDR3800是generic，网件WNDR4300路由器是nand。

	[http://downloads.openwrt.org/snapshots/trunk/ar71xx/generic/](http://downloads.openwrt.org/snapshots/trunk/ar71xx/generic/)

	再选择你的路由器型号，页面搜索 wndr3800，找到了吗。有两个文字供下载，一个文件结尾是 factory.img,适合原厂固件下刷，另一个文件名结尾是sysupgrade.bin,适合已经是OpenWrt系统下刷。
## 4. 刷入固件

不同的路由器刷入方式不同,NETGEAR WNDR3800采用的是官方固件直接刷入.

* 注意事项 : 刷入OpenWRT首先要先给系统进行降级,将版本降至`V1.0.0.16`版本或更低,后面的版本不支持直接刷入,如果强刷,会变砖.
* 刷入后首次启动需要设置root密码,并开启ssh.设置root密码后,会自动开启ssh.
* 刷入成功后,设置网络一定要在`WAN`口设置,不要设置`LAN`口...亲测,设置`LAN`口会失去链接...请不要作死...

## 5. 安装软件

opkg是openwrt里的软件包管理器，类似mac下的brew、Ubuntu下的apt-get和centos下的yum。现在就可以用opkg来像Linux一样安装软件了.

### 更换opkg软件源

编辑`/etc/opkg/distfeeds.conf`文件,将内容替换为如下内容.

```
src/gz chaos_calmer_base http://openwrt.mirrors.ustc.edu.cn/chaos_calmer/15.05.1/ar71xx/generic/packages/base
src/gz chaos_calmer_luci http://openwrt.mirrors.ustc.edu.cn/chaos_calmer/15.05.1/ar71xx/generic/packages/luci
src/gz chaos_calmer_packages http://openwrt.mirrors.ustc.edu.cn/chaos_calmer/15.05.1/ar71xx/generic/packages/packages
src/gz chaos_calmer_routing http://openwrt.mirrors.ustc.edu.cn/chaos_calmer/15.05.1/ar71xx/generic/packages/routing
src/gz chaos_calmer_telephony http://openwrt.mirrors.ustc.edu.cn/chaos_calmer/15.05.1/ar71xx/generic/packages/telephony
src/gz chaos_calmer_management http://openwrt.mirrors.ustc.edu.cn/chaos_calmer/15.05.1/ar71xx/generic/packages/management
```

然后执行`opkg update`刷新列表.

### opkg使用方式

#### 打印帮助

```
opkg -h
```

#### 更新资源列表

```
opkg update
```

#### 列出已安装的包

```
opkg list
```

#### 搜索包

```
opkg search shadowsocks
```

#### 安装软件，以安装curl和wget为例

```
opkg install curl
```
#### 安装本地软件包

```
opkg install /tmp/wget_1.16-1_ramips_24kec.ipk 
```

#### 移除软件

```
opkg remove wget
```


