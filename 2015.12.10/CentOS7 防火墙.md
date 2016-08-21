#CentOS7 防火墙

CentOS 7 的防火墙由之前版本的 `iptables` 换成了 `firewall`

## 1. 关闭防火墙

```
systemctl stop firewalld.service
```


## 2. 关闭开机启动

```
systemctl disable firewalld.service
```


## 3. 安装iptables防火墙

```
yum install iptables-services
```


## 4. 配置iptables防火墙，打开指定端口

略

## 5. 设置iptables防火墙开机启动

```
systemctl enable iptables
```




