# ghost 博客开启 https
## 一.申请 SSL 证书
  
推荐使用`Let’s Encrypt SSL`自签证书.简单迅速.
  
使用方法.

```
git clone https://github.com/letsencrypt/letsencrypt.git
cd letsencrypt
./letsencrypt-auto certonly --standalone --email admin@thing.com -d thing.com -d www.thing.com -d otherthing.net
```


## 二.配置 nginx

```
server {
listen 80;
listen 443;
server_name your.domain.name;
ssl on;
ssl_certificate /etc/letsencrypt/live/your.domain.name/fullchain.pem; #cacert.pem 文件路径
ssl_certificate_key /etc/letsencrypt/live/your.domain.name/privkey.pem; #privkey.pem 文件路径
location / {
proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
proxy_set_header Host $http_host;
proxy_set_header X-Forwarded-Proto $scheme;
proxy_pass http://127.0.0.1:2368;
client_max_body_size 1000m;
}
}
```


## 三.修改 ghost 的配置文件 config.js

```
修改 url: 'https://your.domain.name',
添加 forceAdminSSL: true;
```




