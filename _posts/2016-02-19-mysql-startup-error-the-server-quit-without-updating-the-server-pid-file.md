---
id: 247
title: 'MySQL服务器启动错误 &#8216;The server quit without updating PID file&#8217;'
date: 2016-02-19T23:04:12+08:00
author: Kanaan Austen
layout: post
guid: https://blog.nieyujiang.info/?p=247
permalink: /2016/02/19/mysql-startup-error-the-server-quit-without-updating-the-server-pid-file/
flavour_num_words:
  - 248
views:
  - 6
categories:
  - Linux
  - Mac
---
<!--wp-compress-html-->

<!--wp-compress-html no compression-->

答案一

你遵循brew install mysql的说明了吗？
  
用用户账户来执行以下命令：

<pre class="prettyprint" ><code>unset TMPDIR
mysql_install_db --verbose --user=`whoami` --basedir="$(brew --prefix mysql)" --datadir=/usr/local/var/mysql --tmpdir=/tmp
</code></pre>

若想在另一个文件夹中建立基础表，或者使用了不同的用户运行了mysqld，请查看mysql\_install\_db的帮助文档：

<pre class="prettyprint" ><code>mysql_install_db --help
</code></pre>

或者查看MySQL官方文档：
  
http://dev.mysql.com/doc/refman/5.5/en/mysql-install-db.html
  
http://dev.mysql.com/doc/refman/5.5/en/default-privileges.html
  
比如说你想使用’mysql’作为用户，你需要运行sudo命令：

<pre class="prettyprint" ><code>sudo mysql_install_db ...options...
</code></pre>

然后手动启动mysqld:

<pre class="prettyprint" ><code>mysql.server start
</code></pre>

注意：如果该操作失败的话，你可能是忘记运行前两步操作

答案二

尝试找到后缀名为”.err”的log文件，这里记录了更详细的信息。它可能位于：

<pre class="prettyprint" ><code>/usr/local/var/mysql/your_computer_name.local.err
</code></pre>

或许是由于权限问题：

检查是否有mysql实例正在运行：

<pre class="prettyprint" ><code>ps -ef | grep mysql
</code></pre>

如果是的话，你应该关掉它，或者直接杀掉进程：

<pre class="prettyprint" ><code>kill -9 PID
</code></pre>

其中PID是第一个命令输出的靠近用户名的那个数字（进程ID）

检查 /usr/local/var/mysql/的所有者：

<pre class="prettyprint" ><code>ls -laF /usr/local/var/mysql/
</code></pre>

如果它的所有者是root的话，你应该把它改成mysql或者你的用户名：

<pre class="prettyprint" ><code>sudo chown -R mysql /usr/local/var/mysql/
</code></pre>

答案三

译者注：我是使用该方法解决的。

我在我的Mac上存在同样的问题(我是严格按照brew install的说明来安装的)

删掉下面这个错误文件解决了我的问题：

<pre class="prettyprint" ><code>sudo rm -rf /usr/local/var/mysql/dev.work.err (dev.work is my hostname)
</code></pre>

这个对我起作用是由于dev.work.err是属于_mysql:wheel的，而不是我自己的用户名.更改“错误文件”的所有者可能也会起作用。

答案四

检查所有正在运行的MySQL进程：

<pre class="prettyprint" ><code>$ ps aux | grep mysql

USER PID %CPU %MEM
_mysql 5970 0.0 0.4 ...
</code></pre>

使用下面的命令杀死所有的进程：

<pre class="prettyprint" ><code>$ sudo kill -9 [PID]
</code></pre>

使用第一条命令获得的PID来代替[PID]，比如说：5970

然后重启MySQL服务器：

<pre class="prettyprint" ><code>$ mysql.server start
</code></pre>

<!--wp-compress-html no compression-->

<!--wp-compress-html-->