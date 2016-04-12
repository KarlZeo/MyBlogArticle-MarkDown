---
id: 189
title: 利用EasyEngine脚本2行代码快速安装WordPress网站程序
date: 2016-02-19T22:49:40+08:00
author: Kanaan Austen
layout: post
guid: https://blog.nieyujiang.info/?p=189
permalink: /2016/02/19/use-2-lines-of-code-easyengine-script-to-quickly-install-wordpress-web-site-program/
dsq_thread_id:
  - 4632686827
views:
  - 8
categories:
  - Linux
---
**第一、EasyEngine部署环境准备工作**

目前，EasyEngine一键包脚本环境，只能支持Ubuntu 12.04 14.04、Debian 7  8环境，所以我们在准备VPS系统之前，需要部署好环境。

**第二、EasyEngine两行脚本实现安装环境和WordPress**

EasyEngine是基于Python开发的快速在Ubuntu和Debian发行版安装NGINX服务器，部署支持HTML，PHP，MySQL，HHVM，PageSpeed和WordPress网站环境。

> wget -qO ee rt.cx/ee && sudo bash ee
    
> sudo ee site create <此处填写网站名称> &#8211;wp 

第一行部署EasyEngine环境。

在部署EE环境的时候需要用户名和邮箱，这个用户名就是我们登录WordPress时候的用户，密码会最后生成给我们。然后执行第二行部署WordPress，我们要看清楚了第二行红色的网址是我们需要绑定的域名。

我们可以看到，最后生成的WordPress站点用户名和密码，我们可以登录后台进行管理。这样我们就部署完毕一个站点，如果需要部署第二个站点，只要执行第二行脚本，修改绑定的域名就可以，同样的方法，可以搭建很多很多，是不是很快速？

**第三、EasyEngine常用问题**

我们的网站是部署在/var/www目录对应的域名文件夹中，其中的htdocs文件夹是存储网页文件的。虽然官方也提供在线的插件安装，但是如果我们需要部署WP网站的插件，可以直接从后台在线安装或者FTP上传文件激活。

总结，EasyEngine比较适合我们需要快速部署WordPress网站程序的用户，比如需要在VPS主机环境中快速部署多个站群的，这个方法的确不错，如果我们需要手工学习搭建的，还是按照传统的步骤安装。因为对于新手用户来说，EasyEngine虽然很快，但是我们可能不知道内部构造。