# macOS 使用 Homebrew 配置 PHP 开发环境

## 安装 Homebrew

```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
## 安装 PHP + Apache + MySQL 环境

### 先添加PHP和Apache的仓库

```
brew tap homebrew/apache
brew tap homebrew/php
```

### 安装 PHP , Apache , MySQL

```
brew install homebrew/php/php70 homebrew/apache/httpd24 mysql homebrew/php/phpmyadmin
```

## 配置

### 设置 MySQL 密码

brew安装的MySQL默认是没有密码的.

* 启动MySQL

```
mysql.server start
```

如果遇到错误或者长时间读条的问题

就到 `/usr/local/var/mysql` 目录下,后缀是.local.err的文件.
然后重新启动.如果还是不行,就打开活动监视器,搜索 `mysqld` .然后手动杀掉所有的 `mysqld` 进程.再尝试开启MySQL服务.

* 修改密码

登录MySQL

```
mysql - u root
```

然后输入

```
SET PASSWORD FOR 'root'@'localhost' = PASSWORD('这里写密码');
```

### 配置Apache

* 启用 PHP 7 模块

在配置文件中加入如下几行

配置文件目录: `/usr/local/etc/apache2/2.4/httpd.conf`

```
LoadModule php7_module    /usr/local/opt/php70/libexec/apache2/libphp7.so

<FilesMatch .php$>
    SetHandler application/x-httpd-php
</FilesMatch>
```

然后在 DirectoryIndex 项加入 index.php .

如果设置的目录在桌面,还需要更改Apache所在的用户和组

修改user和grops为 你的用户名和admin.否则没有权限读取桌面.

* 配置 phpmyadmin

在 Apache 配置文件中加入如下几行

```
Alias /phpmyadmin /usr/local/share/phpmyadmin
<Directory /usr/local/share/phpmyadmin/>
Options Indexes FollowSymLinks MultiViews
AllowOverride All
<IfModule mod_authz_core.c>
    Require all granted
</IfModule>
<IfModule !mod_authz_core.c>
    Order allow,deny
    Allow from all
</IfModule>
</Directory>
```

phpmyadmin的配置文件目录: `/usr/local/etc/phpmyadmin.config.inc.php`



