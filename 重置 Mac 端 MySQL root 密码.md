#重置 Mac 端 MySQL root 密码
在 Mac 端使用 brew 安装完 MySQL 后一开始是没有 root 密码的,保险起见,还是改一下 root 密码比较好.

```
mysqladmin -u root -p password
```


然后输入旧密码,新密码,重复输入新密码就 OK 了.



