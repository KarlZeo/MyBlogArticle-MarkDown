#shadowsocks-libev一键安装脚本
**本脚本适用环境：**
  
系统支持：CentOS 32或64位
  
内存要求：≥128M
  
日期：2015年08月01日

**关于本脚本：**
  
一键安装 libev 版的 shadowsocks 最新版本。该版本的特点是内存占用小（600k左右），低 CPU 消耗，甚至可以安装在基于 OpenWRT 的路由器上。
  
**友情提示：如果你有问题，请先参考这篇《[Shadowsocks Troubleshooting](http://teddysun.com/399.html)》后再问。**

**默认配置：**
  
服务器端口：自己设定（如不设定，默认为 8989）
  
客户端端口：1080
  
密码：自己设定（如不设定，默认为teddysun.com）

**客户端下载：**
  
<http://sourceforge.net/projects/shadowsocksgui/files/dist/>

**使用方法：**
  
使用root用户登录，运行以下命令：

wget &#8211;no-check-certificate https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks-libev.sh chmod +x shadowsocks-libev.sh ./shadowsocks-libev.sh 2>&1 | tee shadowsocks-libev.log

安装完成后，脚本提示如下：

Congratulations, shadowsocks-libev install completed! Your Server IP:your\_server\_ip Your Server Port:your\_server\_port Your Password:your_password Your Local IP:127.0.0.1 Your Local Port:1080 Your Encryption Method:aes-256-cfb Welcome to visit:http://teddysun.com/357.html Enjoy it!

**卸载方法：**
  
使用 root 用户登录，运行以下命令：

./shadowsocks-libev.sh uninstall

**其他事项：**
  
客户端配置的参考链接：<http://teddysun.com/339.html>

安装完成后即已后台启动 shadowsocks ，运行：

ps -ef | grep ss-server | grep -v ps | grep -v grep

可以查看进程是否存在。
  
本脚本安装完成后，会将 shadowsocks-libev 加入开机自启动。

**使用命令：**
  
启动：/etc/init.d/shadowsocks start
  
停止：/etc/init.d/shadowsocks stop
  
重启：/etc/init.d/shadowsocks restart
  
查看状态：/etc/init.d/shadowsocks status

**更多版本 shadowsocks 安装：**
  
[Shadowsocks Python版一键安装脚本（CentOS，Debian，Ubuntu）](http://teddysun.com/342.html)
  
[Debian 下 Shadowsocks-libev 一键安装脚本](http://teddysun.com/358.html)
  
[Shadowsocks-go 一键安装脚本（CentOS，Debian，Ubuntu）](http://teddysun.com/392.html)

**更新说明（2015 年 08 月 01 日）：**
  
1、新增自定义服务器端口功能（如不设定，默认为 8989）；
  
**更新说明（2015 年 04 月 30 日）：**
  
1、本脚本会始终安装最新版的 Shadowsocks；
  
2、修改配置文件 /etc/shadowsocks-libev/config.json 同时启用 IPv4 与 IPv6 支持：

{ &#8220;server&#8221;:[&#8220;[::0]&#8221;,&#8221;0.0.0.0&#8243;], &#8220;server\_port&#8221;:your\_server\_port, &#8220;local\_address&#8221;:&#8221;127.0.0.1&#8243;, &#8220;local\_port&#8221;:1080, &#8220;password&#8221;:&#8221;your\_password&#8221;, &#8220;timeout&#8221;:600, &#8220;method&#8221;:&#8221;aes-256-cfb&#8221; }

3、Shadowsocks libev 版不能通过修改配置文件来多端口（只能开启多进程），如果你需要多端口请安装 Python 或 Go 版；

**特别说明：**
  
1、已安装旧版本的 shadowsocks 需要升级的话，需下载本脚本的最新版，运行卸载命令

./shadowsocks-libev.sh uninstall

然后，再次执行本脚本即可安装最新版。

