---
id: 277
title: WordPress 开启全站 https
date: 2016-02-20T12:11:11+08:00
author: Kanaan Austen
layout: post
guid: https://blog.nieyujiang.info/?p=277
permalink: /2016/02/20/open-wordpress-https/
flavour_num_words:
  - 175
dsq_thread_id:
  - 4595372800
views:
  - 10
categories:
  - Linux
---
<!--wp-compress-html-->

<!--wp-compress-html no compression-->

为了对付某运营商的流量劫持和自身的数据安全,给自己的网站上一个 https 小绿锁 还是很有必要的.

一.申请 SSL 证书
  
推荐使用`Let’s Encrypt SSL`自签证书.简单迅速.
  
使用方法.

<pre class="prettyprint" ><code>git clone https://github.com/letsencrypt/letsencrypt.git
cd letsencrypt
./letsencrypt-auto certonly --standalone --email admin@thing.com -d thing.com -d www.thing.com -d otherthing.net
</code></pre>

二.配置 nginx

<pre class="prettyprint" ><code>&lt;br />server {
listen 80;
server_name blog.nieyujiang.info;
#rewrite ^ https://$server_name$request_uri? permanent;

### 使用return的效率会更高
return 301 https://$server_name$request_uri;

}
server {
listen 443;
ssl on;
ssl_certificate /etc/letsencrypt/live/blog.nieyujiang.info/fullchain.pem;
ssl_certificate_key /etc/letsencrypt/live/blog.nieyujiang.info/privkey.pem;

server_name blog.nieyujiang.info;
access_log /var/log/nginx/blog.nieyujiang.info.access.log rt_cache;
error_log /var/log/nginx/blog.nieyujiang.info.error.log;
root /var/www/blog.nieyujiang.info/htdocs;

index index.php index.html index.htm;
include common/php.conf;

include common/wpcommon.conf;
include common/locations.conf;
include /var/www/blog.nieyujiang.info/conf/nginx/*.conf;
}
</code></pre>

三.安装**Easy HTTPS (SSL) Redirection** 插件

本插件的作用就是强制将所有链接重定向至 https;

&nbsp;

<!--wp-compress-html no compression-->

<!--wp-compress-html-->