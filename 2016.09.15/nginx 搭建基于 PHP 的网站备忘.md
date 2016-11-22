# nginx 搭建基于 PHP 的网站备忘

## 安装 nginx

* Ubuntu / Debian

```
sudo apt install nginx
```

* CentOS / Fedora

```
sudo dnf install nginx
```

或者

```
sudo yum install nginx
```

* macOS 

```
brew install nginx
```

## 安装 php-fpm

* Ubuntu / Debian

```
sudo apt install php7.0-fpm
```

* CentOS / Fedora

```
sudo dnf install php7.0-fpm
```

或者

```
sudo yum install php7.0-fpm
```

* macOS 

php中自带fpm

## 配置 php-fpm

修改 `www.conf` 文件.确定fpm运行的端口,默认是`9000`.
启动fpm服务并加入开机启动.

## 配置 nginx


