#重置 MySQL 密码

## 一. 用SET PASSWORD命令

```
mysql -u root
mysql> SET PASSWORD FOR 'root'@'localhost' = PASSWORD('newpasswordword');
```

## 二. 用mysqladmin

```
mysqladmin -u root password "newpassword"
```

如果root已经设置过密码,采用如下方法

```
mysqladmin -u root password oldpassword "newpassword"
```

## 三. 用UPDATE直接编辑user表

```
mysql -u root
mysql> use mysql;
mysql> UPDATE user SET Password = PASSWORD('newpassword') WHERE user = 'root';
mysql> FLUSH PRIVILEGES;
```

在丢失root密码的时候,可以这样.
基本的思路是，以安全模式启动mysql,这样不需要密码可以直接以root身份登录,然后重设密码.
首先停掉 `mysql` 的服务.

```
service mysql stop
```

然后以安全模式启动 `mysql`. `--skip-networking`是防止远程网络直接无密码连接数据库.

```
mysqld_safe --skip-grant-tables --skip-networking &
```
然后登录 `mysql`.

```
mysql -u root
```

重设密码.

```
mysql> UPDATE user SET password=PASSWORD("new password") WHERE user='root';
mysql> FLUSH PRIVILEGES;
```


