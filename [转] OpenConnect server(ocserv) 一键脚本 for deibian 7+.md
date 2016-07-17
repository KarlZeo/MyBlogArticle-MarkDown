# [转] OpenConnect server(ocserv) 一键脚本 for deibian 7+

该脚本在deibian 7+/ubuntu 14.04-15.10(2015-10-31)上进行过测试，默认使用密码方式登录，思科anyconnect客户端可连可用。

AnyConnect是思科的安全远程接入解决方案，之前只有思科的设备才支持。

ocserv(OpenConnect server)是一个OpenConnect SSL 协议服务端，0.3.0版后兼容使用AnyConnect SSL 协议的终端。

官方主页：<http://www.infradead.org/ocserv/>

2015年7月6日
  
更新和提示：
  
1，默认使用ocserv的0.10.6版本，由于移除了服务端路由规则数量限制，脚本不再询问路由规则限制数。
  
2，自签证书全部使用sha256签名算法，且完善证书链。
  
3，增加支持ubuntu 14.10、15.04。（但不建议使用非LTS版本ubuntu）
  
4，证书登录方式增加支持自定义客户端证书的CN名。
  
5，添加了更加完整的安装日志。
  
6，更新启动管理脚本，增加debug模式，下文说明。
  
7，支持用户名密码登录和证书登录同时开启，下文说明。
  
8，增加了相同客户端证书可以登录多个服务器的方案，下文说明。
  
9，修复一些其他小问题。
  
2015年5月1日
  
更新和提示：
  
1，编译安装freeradius-client-1.1.7，便于freeradius认证。（/etc/radiusclient/radiusclient.conf）
  
2，编译安装lz4。（/usr/local）
  
3，随机字符串获取剔除容易识别错误的字符例如0和O等等。
  
4，增加DH parameters。
  
5，关于GSSAPI认证，开启支持下文说明。
  
6，兼容debian 8 (jessie)。
  
7，在没有卸载依赖的情况下，支持平滑升级降级，升降级之后原来用户数据保留；也可以选择强制重装，抹掉原来数据。
  
2015年4月8日
  
更新和提示：
  
1，允许自定义客户端证书的到期日期。
  
2，默认从github编译安装依赖包lz4，避免某些情况下会破坏系统，但仍然可以选择强制从debian Jessie更新liblz4-dev。
  
3，增加对ubuntu 14.04的支持 。
  
2015年3月25日
  
更新与提示：
  
1，增加了ocserv最新版本检测，默认推荐使用0.10.1版本 。
  
2，如果为了稳定使用，这里并不推荐使用最新版本，有些最新发行版由于存在严重bug很快被更新的版本替代。
  
3，增加支持证书登录以及吊销证书。
  
4，默认开启lz4压缩，据说能极大提升速度。
  
5，默认是tcp和udp同时开启，若速度不佳，可在安装时选Only use tcp-port，或在配置文件里面注释掉udp端口。
  
6，曾经使用过该脚本安装的朋友，可以通过下面提到的命令升级重装。
  
2015-01-27
  
更新：依然使用0.8.9版本进行编译安装，增加了一些自定义选项，但不支持证书登录。

由于各种依赖较新，debian 7以下不支持。openvz需要支持打开tun/tap服务。

关于这个一键脚本的github放置点

<https://github.com/fanyueciyuan/eazy-for-ss/tree/master/ocservauto>

编译安装总结（jessie）

![install-su](https://lh3.googleusercontent.com/-J3LtgTzF6xA/V4t6XLsjTlI/AAAAAAAAAxE/J8HVlWm6dTI/I/install-sum.png)


一，安装步骤：

1，安装与调试

如果这是纯净新系统的话，请先更新一下系统。

```
apt-get update && apt-get upgrade -y
```


首次安装，终端输入以下命令

```
wget git.io/p9r8 --no-check-certificate -O ocservauto.sh&&bash ocservauto.sh
```


如果您以前使用了该脚本进行安装，只需要输入下面命令更新（只更新相关脚本，服务器不会更新）

```
wget git.io/ocservauto -O- --no-check-certificate|bash -
```


如果使用自动安装，默认是使用用户名和密码登录，只需要输入初始用户名和密码，回车即可自动安装完成。

如果使用自定义安装，请输入自己的要求来完成安装。

下面是进入脚本之后一些选项说明解释。

![p-1](https://lh3.googleusercontent.com/-LMIPrngMJOs/V4t6XXX2hHI/AAAAAAAAAxI/vYlbI0hV9Xk/I/p-1.png)
![p-2](https://lh3.googleusercontent.com/-ZqWH9kh499o/V4t6XVlDQzI/AAAAAAAAAxM/Xsr_V4uBHpE/I/p-2.png)
![p-3](https://lh3.googleusercontent.com/-hIRRzkpUsjI/V4t6XsyfJnI/AAAAAAAAAxQ/Ri2keRT9GwI/I/p-3.png)


如果安装顺利，最后给出您的相应信息，例如

![install-ok](https://lh3.googleusercontent.com/-_WczTA1SJrM/V4t6Yi17LoI/AAAAAAAAAxo/J586z5_CtY4/I/install-ok.png)


如果安装失败可以查阅安装日志，即脚本所在文件夹的ocinstall.log文件，可以使用下面命令逐步阅读

```
more ocinstall.log
```


空格键，向下滚动一屏；Ctrl+b，返回上一屏；q，退出。

一般情况下安装成功之后，服务器就在启动状态了。

这里可以简单使用本地浏览器查看服务器信息，在本地浏览器输入https://IP或域名:（英文冒号）端口

![ca-256](https://lh3.googleusercontent.com/-ciGSgDLpOB0/V4t6X9jZagI/AAAAAAAAAxY/0lwtf6Ox-zk/I/ca-256.png)


如果您仍然无法连到服务器或者出现其他问题，那么请使用debug模式。

如果您以前使用了该脚本进行安装，这里请先通过前面所说的，更新一下脚本。

首先关闭服务器，然后开启调试模式

```
/etc/init.d/ocserv stop
/etc/init.d/ocserv debug
```

![debug](https://lh3.googleusercontent.com/-i_5WMH8bc3Y/V4t6YPqYzvI/AAAAAAAAAxc/Yx0z5BdzqzU/I/debug.png)


此时不要关闭终端，使用客户端登录服务器，在终端屏幕下就会显示即时日志，以供调试改错。

2，简单用户管理

a，用户名密码验证方式

若要新建可用用户，输入以下命令

```
sudo ocpasswd -c /etc/ocserv/ocpasswd 999
```


这里的 “999”是新建的用户名。接着输入两次同样的密码，完成新建用户。

b，证书登录方式

所有用户的p12证书文件可以在放置脚本的目录下找到，导入证书时请输入自己设定的密码。

新建客户证书用以下命令

```
bash ocservauto.sh gc
```

![g](https://lh3.googleusercontent.com/-m2YFQkZNSIk/V4t6YePb_FI/AAAAAAAAAxg/8kVRhNHOAo4/I/gc.png)
  
![gc-resut](https://lh3.googleusercontent.com/-afZus_v5H6M/V4t6Ye4c0bI/AAAAAAAAAxk/UtSm50Yk2as/I/gc-resutl.png)


吊销客户证书请使用下面命令

```
bash ocservauto.sh rc
```

![install-ok](https://lh3.googleusercontent.com/-_WczTA1SJrM/V4t6Yi17LoI/AAAAAAAAAxo/J586z5_CtY4/I/install-ok.png)


3，脚本其他参数说明

a，平滑升级ocserv

请输入以下命令，原来的用户数据都会保留

```
bash ocservauto.sh ug
```


b，强制重装ocserv

请输入以下命令，注意这会使您的用户数据和配置丢失

```
bash ocservauto.sh ri
```


c，同时开启证书登录和用户名密码登录

请务必首先选择任意一种登录方式来完成安装，接着再使用下面命令

```
bash ocservauto.sh pc
```


d，关于相同客户端证书可以登录多个服务器的方案

假定我们有三台服务器ABC。

在A服务器上，通过本脚本安装ocserv并选择使用证书登录方式。

于/etc/ocserv目录下可以找到ca-cert.pem文件。这里复制备用，ca-cert.pem不用保密，可以直接挂在公网上。

在BC服务器上下载本脚本，并且请在同文件夹下放置A服务器上的ca-cert.pem，然后执行

```
bash ocservauto.sh occ
```


这里ABC服务器共用了A服务器的验证证书。

想要获取新证书，请在A服务器上执行

```
bash ocservauto.sh gc
```


也可以使用该客户端证书登录BC服务器。

如想要吊销证书，请在A服务器上执行

```
bash ocservauto.sh rc
```


吊销所有想要吊销的证书。

由于不支持在线吊销证书列表，所以必须还要把A服务器上的/etc/ocserv/crl.pem文件同时复制到BC服务器相同位置，且把ocserv的配置文件中的

```
#crl = /etc/ocserv/crl.pem
```


去掉注释，最后重启BC服务器的ocserv。
  
二，使用步骤

这里以安卓为例，由于是自签证书，需要关掉客户端设置中的“阻止不信任的服务器”。

![1535EFFCDF4C46C6F0B7F03D72D24CE1_LARGE_720_1280](https://lh3.googleusercontent.com/-2tWQGTTQvvw/V4t6ZCNEsNI/AAAAAAAAAxw/qg-UZ2VRD8M/I/1535EFFCDF4C46C6F0B7F03D72D24CE1_LARGE_720_1280.jpeg)


服务器需要填写的是自己服务器的地址加端口，例如9.9.9.9:999，必须要填写自己的端口！

关于客户端的获取，安卓、IOS、WindowsPhone在官方市场可以获取，特殊说明的是WindowsPhone是BETA版，如下

<http://www.fanyueciyuan.info/jsxj/wp-anyconnect.html>

三，附加说明

1，所有配置文件统一放到了/etc/ocserv/文件夹下，管理脚本为/etc/init.d/ocserv 。自行修改配置后，可以使用下面命令重启服务。

```
/etc/init.d/ocserv restart
```


2，该脚本下ocserv的证书逻辑。

a，用户名密码登录

自签CA（证书授权中心），取得ca-cert.pem（不需要保密，类比公钥）和ca-key.pem（需要保密，类比私钥）。

CA签发信任服务器证书，取得server-cert.pem（不需要保密，类比公钥）、server-key.pem（需要保密，类比私钥）。

该模式下，密码库是/etc/ocserv/ocpasswd文件。

如果想使用购买的服务器证书，请参考Nginx服务器证书配置，只需将对应的crt、key 文件重命名为server-cert.pem、server-key.pem，并覆盖到/etc/ocserv/文件夹下面。

b，证书登录

自签CA（证书授权中心），取得ca-cert.pem（不需要保密，类比公钥）和ca-key.pem（需要保密，类比私钥）。

CA签发信任服务器证书，取得server-cert.pem（不需要保密，类比公钥）、server-key.pem（需要保密，类比私钥）。

CA签发信任客户端证书，最终取得username.p12。

这里证书授权中心的ca-cert.pem既当作服务器证书的根证书，也当作客户端证书的验证证书。

由于CA证书当作验证证书，签发客户端证书就需要这个ca-key.pem，可以比同为密码库。

如果想使用购买的服务器证书，请参考Nginx服务器证书配置，只需将对应的crt、key 文件重命名为server-cert.pem、server-key.pem，并覆盖到/etc/ocserv/文件夹下面。

3，改善优化

修改的参数都在/etc/ocserv/ocserv.conf文件中。

a，对于某些移动宽带、长城带宽等，往往经过了很多重NAT，容易出现连接成功但是无法打开网页情况，请改小dpd、mobile-dpd数值。

b，如果vps对于本地延迟甚高，取消注释output-buffer项。



