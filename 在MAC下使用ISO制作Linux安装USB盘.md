# 在MAC下使用ISO制作Linux安装USB盘
## 1. 在 `terminal` 将 ISO 镜像转换为 DMG 格式

命令:


```
hdiutil convert -format UDRW -o ~/Desktop/arch.dmg ~/Desktop/archlinux-2016.05.01-dual.iso
```

终端输出:

```
正在读取Master Boot Record（MBR：0）…
正在读取ARCH_201605                     （Apple_ISO：1）…
正在读取（Type EF：2）…
..........
正在读取ARCH_201605                     （Apple_ISO：3）…
........................................................................................................................................................................................................
已耗时： 2.184s
速度：336.0M 字节/秒
节省：0.0%
created: /Users/Kanaan/Desktop/arch.dmg
```

## 2. 插入USB盘，然后在终端下，查找该盘的设备名：

命令:

```
diskutil list
```

终端输出:

```
/dev/disk0 (internal, physical):
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme                        *500.3 GB   disk0
   1:                        EFI EFI                     209.7 MB   disk0s1
   2:          Apple_CoreStorage Mac                     499.4 GB   disk0s2
   3:                 Apple_Boot Recovery HD             650.0 MB   disk0s3
/dev/disk1 (internal, virtual):
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:                  Apple_HFS Mac                    +499.1 GB   disk1
                                 Logical Volume on disk0s2
                                 69D0762B-CC13-4BF4-8A07-A149B355D29B
                                 Unlocked Encrypted
/dev/disk2 (external, physical):
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:     FDisk_partition_scheme                        *15.7 GB    disk2
   1:             Windows_FAT_32 J_CCSA_X64F             15.7 GB    disk2s4
```

以上显示该盘的设备名是： `/dev/disk2`

## 3. 卸载USB盘（插入时已经自动挂载了），但是不要推出。

命令:

```
diskutil umountDisk /dev/disk2
```

终端输出:

```
Unmount of all volumes on disk2 was successful
```

## 4. 将上面生成的 DMG 镜像烧录到 USB 设备

命令

```
sudo dd if=arch.dmg of=/dev/disk2 bs=1M
```

终端输出:

```
Password:
734+0 records in
734+0 records out
769654784 bytes (770 MB, 734 MiB) copied, 486.483 s, 1.6 MB/s
```

此处要千万注意，指定的of别写错了，否则悔之晚矣。另外，of参数指定的设备名，可以用上面找到的/dev/disk1，也可以用/dev/rdisk1，此处的“r”据说会写入较快。
 
另外，如果报错：“dd: Invalid number `1m'”，可能是使用的不同版本的dd，可以换为bs=1M试试。
 
如果报错：“dd: /dev/diskN: Resource busy”，可能是上面的步骤中没有完成卸载USB盘。

## 5. 推出USB盘。在上面复制之后，系统可能会报错，“此电脑不难读取能插入的磁盘”，不必理会，直接推出即可。

或者使用命令推出:

```
diskutil eject /dev/disk2
```


