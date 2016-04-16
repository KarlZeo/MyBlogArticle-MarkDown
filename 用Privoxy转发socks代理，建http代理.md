#用Privoxy转发socks代理，建http代理

有些软件不支持socks代理，只支持http代理。不像火狐那样都支持，于是有的时候要建http代理。

如果您有socks代理，想做一个http代理的话，这篇文章可能会有帮助。

**安装Privoxy**



```
brew install Privoxy
```


**配置Privoxy**

配置文件默认是 `/usr/local/etc/privoxy/config(mac)` 或 `/etc/privoxy/config(linux)`
  
编辑它增加一行：



```
forward-socks5 / 127.0.0.1:1080 .
```




forward-socks5代表转发到socks5代理，/代表所有的URL都转发(也可以在这里写url patten)，127.0.0.1:1080是socks代理的位置，最后的一点.代表没有http代理，具体请上官网查阅。

保存即生效。

现在的127.0.0.1:8118就是一个http代理了。8118是privoxy默认的端口。

**开机自启**



```
ln -sfv /usr/local/opt/privoxy/*.plist ~/Library/LaunchAgents
```




