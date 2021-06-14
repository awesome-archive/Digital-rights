---
---

# 在 macOS 和 Linux 上彻底删除/清空磁盘

> 缘起：之前的 2017年文章：[Digital-rights/2017-06-13-關於徹底刪除這件事](https://github.com/mdrights/Digital-rights/blob/master/W%E7%89%A9%E7%90%86%E5%AE%89%E5%85%A8/2017-06-13-%E9%97%9C%E6%96%BC%E5%BE%B9%E5%BA%95%E5%88%AA%E9%99%A4%E9%80%99%E4%BB%B6%E4%BA%8B.md)，现在仍然有效，讲解了闪存型存储（包括 U盘、SD卡、SSD 固态硬盘）的彻底删除文件是很难的。因此现在我们继续探讨一下怎样在那上面安全地消除你不想要的文件。其中一个办法就是：**对整块磁盘或分区覆盖（随机的）数据**。  

## 注意（Disclaimer）  

本文介绍的方法会删除你磁盘或分区里的所有数据，并且会对数据恢复操作有很大的难度，因此请对重要的数据及时备份/转移。本文不对也无法对误删的数据和其他连带损失（如系统无法启动）负责。  

## 基本策略

因为闪存型存储自己的机制，很难确保单个或多个文件数据真正被抹去了（“忘记它放哪儿了就等于删除啦”）。那我们就得把整块磁盘覆盖满满的随机数据。  

但通常我们的磁盘上还有别的重要数据不能删，所以更好的做法是：  

- 给磁盘划多些分区，这样覆盖一个分区就不会影响其他的分区；
- 重要数据存储在小容量的存储设备（如 8G/16G U盘）上，比较方便。


## 用什么数据覆盖

一般来说，在 macOS/Linux 系统上有两种数据可以自动生成用来覆盖磁盘/分区的空间：`/dev/zero` 和 `/dev/urandom`  

- `/dev/zero`：即一种叫“zero”的数据，可以把磁盘/分区齐刷刷地刷成相同的样子。特点是很快，但对于有些“高级”的SSD硬盘，这一招并不奏效，因为它会把重复的数据压缩，并没有真实地覆盖所有的磁盘空间。  
- `/dev/urandom`：由系统持续生成（半）随机杂乱的数据，这样再覆盖到磁盘/分区，显得磁盘更杂乱无章。  


## macOS 操作命令

**注**: macOS 一般不建议对其自己的内置硬盘这样操作（因为通常不对内置的 data 分区再进行分区，除非你知道怎么操作及操作后果），因此我们来对外置磁盘进行如下操作。  

- 先确定你的外置磁盘/U盘的编号：
```
  diskutil list   (查看并找出你的磁盘编号)   
  diskutil unmountDisk /dev/diskX   (这里的 X 要换成你实际的编号；系統會默認掛載，我們卸載它；或者在桌面对磁盘图标右键弹出)
```

- 执行命令！
```
  sudo dd bs=4096 if=/dev/urandom of=/dev/rdiskX    (注意請看清你的磁盘编号; 会要求输入你的登录密码)
```
  注意这个 dd 命令不会任何进度条展示，且时间会比较久～  

见到这样的输出就说明命令完成，覆盖完了：    
```
dd: writing to ‘DiskX’: No space left on device
20481+0 records in
20480+0 records out
10485760 bytes (10 MB, 10 MiBcopied, 2.29914 s, 4.6 MB/s)
```


## Linux 操作命令 

Linux 系统里你可以随意处置/分配你的磁盘分区。  

- 先确定你的磁盘/U盘的编号：
```
  lsblk
  sudo umount /mnt/XXX  (如果你的系統自動掛載了，需要卸載它；/mnt/XXX 是它的挂载目录)
```

- 执行命令！
```
  sudo dd bs=4096 if=/dev/urandom of=/dev/sdXY    (注意請看清你的磁盘编号; 会要求输入你的登录密码)
```
  注意这个 dd 命令不会任何进度条展示，且时间会比较久～  



## 如果你只想擦除磁盘/分区的空余空间

如果你之前在某个磁盘/分区删除过文件，但因为还有其他文件不能让你把整个磁盘/分区重新覆盖一次，那么你可以擦除一个磁盘/分区的空余空间（free space）而不把里面现有的文件也擦除掉。

你可以尝试：  
```
(macOS)
    cat /dev/urandom > /dev/rdisk"XY"
(Linux) 
    cat /dev/urandom > /dev/sd"XY"
```

直到：  
```
  cat: write error: No space left on device
```


## 注意事项

- 用无意义的数据覆盖整个磁盘/分区是个不错的方法，但对于分区，如果你之前移动过分区或更改过分区大小，那这个效果就会打折扣（因为可能就会有文件数据落在了当前分区以外的地方啦）。  

- 如果你仍然想只删除单个/多个文件，那么需要更多的命令行技巧，详见：[Securely wipe disk/Tips and tricks - ArchWiki](https://wiki.archlinux.org/title/Securely_wipe_disk/Tips_and_tricks#Wipe_a_single_file)


## 参考

- [Securely wipe disk - ArchWiki](https://wiki.archlinux.org/title/Securely_wipe_disk)

- [Solid state drive/Memory cell clearing - ArchWiki](https://wiki.archlinux.org/title/Solid_state_drive/Memory_cell_clearing)
