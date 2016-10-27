# 私人 Git 代码托管平台 Gogs 搭建实录

## 1. 简介 

Gogs (Go Git Service) 是一款极易搭建的自助 Git 服务。Gogs 的目标是打造一个最简单、最快速和最轻松的方式搭建自助 Git 服务。使用 Go 语言开发使得 Gogs 能够通过独立的二进制分发，并且支持 Go 语言支持的 所有平台，包括 Linux、Mac OS X、Windows 以及 ARM 平台。

## 2. 搭建过程 

### 2.1 安装 Golang 开发环境 

#### 2.1.1 安装 GOVM go语言版本管理器

  * 安装必要的环境控件及依赖(以 Debian 为例)

```
sudo apt-get install git build-essential curl
```


  * 然后下载一键安装脚本

```
curl -L git.io/govm | python - setup
```


脚本执行完毕后会在`Home`目录下产生一个`.govm`的隐藏文件夹.

  * 添加环境变量

```
export GOVM_ROOT=$HOME/.govm
export PATH=$GOVM_ROOT/versions/current/bin:$PATH
```


  * 重新加载配置文件

```
source ~/.zshrc
```


#### 2.1.2 使用 GOVM 安装 golang 

  * 安装 golang 

```
govm install go1.4.3
```


  * 使用当前安装的 golang 版本

```
govm use go1.4.3

```


  * 配置 golang 环境变量

```
export GOROOT=$HOME/local/go
export GOPATH=$HOME/go
export PATH=$PATH:$GOROOT/bin:$GOPATH/bin
```


刷新配置文件
  
``



## 1. 简介

Gogs (Go Git Service) 是一款极易搭建的自助 Git 服务。Gogs 的目标是打造一个最简单、最快速和最轻松的方式搭建自助 Git 服务。使用 Go 语言开发使得 Gogs 能够通过独立的二进制分发，并且支持 Go 语言支持的 所有平台，包括 Linux、Mac OS X、Windows 以及 ARM 平台。

## 2. 搭建过程 

### 2.1 安装 Golang 开发环境 

#### 2.1.1 安装 GOVM go语言版本管理器 

  * 安装必要的环境控件及依赖(以 Debian 为例)

```
sudo apt-get install git build-essential curl
```


  * 然后下载一键安装脚本

```
curl -L git.io/govm | python - setup
```


脚本执行完毕后会在`Home`目录下产生一个`.govm`的隐藏文件夹.

  * 添加环境变量

```
export GOVM_ROOT=$HOME/.govm
export PATH=$GOVM_ROOT/versions/current/bin:$PATH
```


  * 重新加载配置文件

```
source ~/.zshrc
```


#### 2.1.2 使用 GOVM 安装 golang 

  * 安装 golang 

```
govm install go1.4.3
```


  * 使用当前安装的 golang 版本

```
govm use go1.4.3

```


  * 配置 golang 环境变量

```
export GOROOT=$HOME/local/go
export GOPATH=$HOME/go
export PATH=$PATH:$GOROOT/bin:$GOPATH/bin
```


刷新配置文件
  
`` 

### 2.2 下载安装 Gogs 源代码 

#### 2.2.1 下载 Gogs 并安装依赖 

```
go get -u github.com/gogits/gogs
```


#### 2.2.2 构建主程序 

```
cd $GOPATH/src/github.com/gogits/gogs
go build
```


#### 2.2.3 测试安装 

```
./gogs web
```


### 2.3 创建数据库

```
mysql -u root -p
```


输入管理员密码.然后创建一个数据库.

```
 create user &#39;gogs&#39;@&#39;localhost&#39; identified by &#39;passcode&#39;;
 
 grant all privileges on gogs.* to &#39;gogs&#39;@&#39;localhost&#39;;
 
 flush privileges;
 
 exit;
```


### 2.4 配置域名

  * nginx 反代

```
server {
    server_name 域名或IP;
    listen 80; # 或者 443，如果你使用 HTTPS 的话
    # ssl on; 是否启用加密连接
    # 如果你使用 HTTPS，还需要填写 ssl_certificate 和 ssl_certificate_key

    location / { # 如果你希望通过子路径访问，此处修改为子路径，注意以 / 开头并以 / 结束
        proxy_pass http://127.0.0.1:3000/;
    }
}
```


然后进入 `/etc/nginx/sites-enabled` 中，执行 `ln -s ../sites-available/配置文件名` 启用这个配置文件。
  
最后重启 `nginx`就好了，Ubuntu 下是 `sudo service nginx restart`。

### 2.5 配置 SSl 加密 

在 custom/conf/app.ini 文件中修改下列配置选项（以下仅为示例）

```
[server]
PROTOCOL = https
ROOT_URL = https://try.gogs.io/
CERT_FILE = custom/https/cert.pem
KEY_FILE = custom/https/key.pem
```


如果您想要使用自签名的 HTTPS，则可以使用下列命令来生成所需文件（需要使用构建标签 cert 或直接从官方下载二进制）：

```
./gogs cert -ca=true -duration=8760h0m0s -host=myhost.example.com
```


## 3. 创建守护进程

### 3.1 使用启动脚本

[Debian 启动脚本](https://github.com/gogits/gogs/blob/master/scripts/init/debian/gogs)
  
[Centos 启动脚本](https://github.com/gogits/gogs/blob/master/scripts/init/centos/gogs)

### 3.2 使用Systemd 服务 

在 GitHub 上的 Gogs 仓库有一个 [systemd 服务模版文件](https://github.com/gogits/gogs/blob/master/scripts/systemd/gogs.service)，您需要做出一定的修改才能够使用它：

  * 更新 `User`、`Group`、`WorkingDirectory`、`ExecStart` 和 `Environment` 为相对应的值。其中 `WorkingDirectory` 为您的 `Gogs` 实际安装路径根目录。
  * [可选] 如果您 Gogs 安装示例使用 `MySQL/MariaDB`、`PostgreSQL`、`Redis` 或 `memcached`，请去掉相应 `After` 属性的注释。
  
    当您完成修改后，请将文件保存至 `/etc/systemd/system/gogs.service`，然后通过 `sudo systemctl enable gogs` 命令激活，最后执行 `sudo systemd start gogs`。

您可以通过 `sudo systemd status gogs -l` 或 `sudo journalctl -b -u gogs` 命令检查 Gogs 的运行状态。

## 4. 安装 

在 Gogs 服务运行起来以后,在浏览器输入你的 `http://IP地址:3000` 来访问或者使用你配置的域名来访问.初次访问会进入安装界面.将你在服务器配置的参数填进去就行了,过一会就可以进入主界面,这时候Gogs 就搭建好了.



