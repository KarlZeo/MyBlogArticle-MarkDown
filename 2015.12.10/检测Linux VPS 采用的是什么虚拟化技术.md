# 检测Linux VPS 采用的是什么虚拟化技术

## 1. 下载源代码 

首先,先来[virt-what的源代码网站](https://people.redhat.com/%7Erjones/virt-what/files/)下载最新的 `virt-what` 源代码.
  
目前最新的版本是 `virt-what-1.15` .

```
wget http://people.redhat.com/~rjones/virt-what/files/virt-what-1.15.tar.gz
```


## 2. 编译安装 

```
tar zxvf virt-what-1.15.tar.gz
cd virt-what-1.15/
./configure
make
make install
```


## 3. 检测 

执行 `virt-what`命令,就会输出当前 VPS 的架构.

```
virt-what
```




