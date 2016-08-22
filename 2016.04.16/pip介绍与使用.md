# pip介绍与使用

## 1. 介绍

pip 是一个安装和管理 Python 包的工具，python安装包的工具有easy\_install, setuptools, pip，distribute。使用这些工具都能下载并安装django。，而pip是easy\_install的替代品。在CPython解释器，pypy解释器，可以很好地工作

## 2. 使用

### 2.1 安装pip

安装和升级之前，先下载 [get-pip.py](https://bootstrap.pypa.io/get-pip.py)
  
然后使用下面的命令：

```
python get-pip.py
```


不过注意一下，linux或osX下，需要权限，使用下面的命令，输入密码后即可。

```
sudo python get-pip.py 
```


windows下需要管理员权限启动终端。
  
如果你还没有安装了setuptools，get-pip.py 会帮你安装。
  
如果你已经安装了setuptools，运行下面的命令进行升级。

```
pip install -U setuptools
```


windows下，注意将pip路劲加到系统的path中，原因就不解释了吧。

### 2.2 升级pip

Linux or OS X系统，运行下面的命令:

```
pip install -U pip
```


windows系统运行下面的命令：

```
python -m pip install -U pip
```


### 2.3 安装包 

使用下面的命令来安装包

```
pip install SomePackage            # latest version
pip install SomePackage==1.0.4     # specific version
pip install &#39;SomePackage&gt;=1.0.4&#39;     # minimum version
```


要看更多地例子，可以看这里 `pip install`

例如我要安装Django，用下面的一条命令即可，方便快捷。

```
pip install Django==1.7
```




