#Shadowsocks 开启 chacha20 加密方式
## 关于 chacha20 加密算法 {#toc_0}

Shadowsocks的作者推荐的加密算法是aes-256-cfb，但是使用手机和openwrt的路由器来说，压力还是不小，于是人们就创造了salsa20这个算法，这个算法比起rc4，足足快了两倍，而安全性也大大加强了，而谷歌，作为手机系统的老大，又对salsa20进行了改造，创造了chacha20这一算法，这一算法在ARM平台上的速度是惊人的，而chacha20相对于他的前任在速度和安全性的方面又有了很大提升。

## 安装 {#toc_1}

```
apt-get install m2crypto
wget https://download.libsodium.org/libsodium/releases/LATEST.tar.gz
tar zxf LATEST.tar.gz
cd libsodium*
./configure
make && make install
#修复关联
echo /usr/local/lib &gt; /etc/ld.so.conf.d/usr_local_lib.conf
ldconfig
```


## 修改配置文件 {#toc_2}

把你的 ss 加密方式改成 chacha20 ,再试试速度吧.



