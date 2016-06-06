# 在linux系统中配置java环境变量的三种方法
在linux系统中配置Java环境变量的三种方法：
以 jdk-8u91-linux-x64.tar.gz 为例.

### 1.修改/etc/profile
如果是本机开发的话,推荐使用这种方法,因为所有的用户 shell 都可以使用这些环境变量.但是有可能会带来安全问题.

* 用 vim 打开/etc/profile 

```
vim /etc/profile
```

* 加入如下内容

```
JAVA_HOME=/usr/loacl/bin/jdk1.8.0_91
PATH=$JAVA_HOME/bin:$PATH
CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
export JAVA_HOME
export PATH
export CLASSPATH
```

* 重新登录

### 2.修改当前用户 shell 配置文件
这种方案比较安全,可以将环境变量权限控制到用户.以 zsh 为例

* 用 vim 打开 .zshrc 文件

```
vim .zshrc
``` 

* 在 .zshrc 文件中加入如下代码

```
set JAVA_HOME=/usr/loacl/bin/jdk1.8.0_91
export JAVA_HOME
set PATH=$JAVA_HOME/bin:$PATH
export PATH
set CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
export CLASSPATH
```

* 重新载入配置文件

```
source .zshrc
```
### 3.直接在shell下设置变量
换个 shell 就没用了.

```
export JAVA_HOME=/usr/loacl/bin/jdk1.8.0_91
export PATH=$JAVA_HOME/bin:$PATH
export CLASSPATH=.:$JAVA_HOME/lib/dt.jar:$JAVA_HOME/lib/tools.jar
```


