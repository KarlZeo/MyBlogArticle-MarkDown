#阻止 DHCP 修改 resolv.conf 文件

对于使用 DHCP 的用户来说，很多时候你需要修改`/etc/resolv.conf`来使用其他的 DNS 服务器。那么，经过了一段时间（或者是经过了机器重启）之后，你会发现你所修改的`/etc/resolv.conf`文件会被恢复为原来的样子。

以下教程讲述了三个阻止 DHCP 修改`/etc/resolv.conf`文件的方法，适用于 Debian 或者是 Ubuntu。

### 把接口设置为静态

  * 在一台云 VPS 上，我十分不建议你使用这种方式。
  * 如果使用这种方式，你可能会发现重启的过程（直到你可以通过 SSH 连接）会更加长一些。

首先，我们需要直到我们的 IP 地址，网络掩码以及网关地址。使用下面的命令：

```
ifconfig | grep "inet addr" | head -n 1 | awk '{print $2, $4}'
```


译者注：Debian 8 的可能是下面这条命令

```
ifconfig | grep "inet Adresse" | head -n 1 | awk '{print $2, $4}'
```


这会显示出服务器的 IP 地址以及网络掩码。让我们来看一看输出

```
addr:1.2.3.4 Mask:255.255.254.0
```


译者注：Debian 8 的可能是下面这条输出

```
Adresse:1.2.3.4 Maske:255.255.254.0
```


服务器的 IP 地址就是`1.2.3.4`，子网掩码就是`255.255.254.0`

运行下面这条命令来获得网关地址。

```
vim /etc/network/interfaces
```


在这个例子中，我们假定网关地址就是`1.2.3.1`

现在我们已经有了IP/子网掩码/网关地址了，修改`/etc/network/interfaces`文件

```
&lt;code class=" hljs "&gt;vim /etc/network/interfaces
```


作出下面的修改

```
# Comment out this line
# iface eth0 inet dhcp

# Add these contents
iface eth0 inet static
address 1.2.3.4
mask 255.255.254.0
gateway 1.2.3.1

```


**请记住，你必修将上面的IP等数据改为你服务器实际的数据。**

保存并关闭，然后重启 VPS 。

### 写保护你的 DNS 服务器

通过修改`/etc/resolv.conf`来修改你的 DNS 服务器。一旦你作出了修改，写保护这个文件

```
chattr +i /etc/resolv.conf
```


这个`+i`的选项就是为文件`/etc/resolv.conf`添加了写保护，因此任何人都不可以修改他，甚至是 root 用户也不行！

如果你需要取消写保护，使用下面的命令：

```
chattr -i /etc/resolv.conf
```


### 使用 DHCP 钩子

这是我最推荐使用的方法。

修改`/etc/dhcp/dhclient-enter-hooks.d/nodnsupdate`文件。

```
vim /etc/dhcp/dhclient-enter-hooks.d/nodnsupdate
```


作出以下的修改

```
#!/bin/sh
make_resolv_conf(){
:
}
```


保存并退出

给文件`nodnsupdate`添加可执行权限

```
chmod +x /etc/dhcp/dhclient-enter-hooks.d/nodnsupdate
```


重启系统，现在你就可以任性地修改`/etc/resolv.conf`文件而且不会担心被回滚了。



