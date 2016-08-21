#  windows查看损坏系统的IP地址配置文件 
可以把硬盘挂在其他的机器上(**系统版本必须大于等于当前系统版本**)，在此硬盘的`system32`下找到`regedt32`，进入损坏的操作系统的注册表。 
然后找到下面的东西：    

```
HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Services\Tcpip\Parameters\Interfaces
```


