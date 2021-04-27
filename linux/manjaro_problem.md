### 1.csnd加载速度

### 2.clash服务加载速度

### 3.tweak全屏可用，半屏不好用 

解决：tweak中 windows titlebar 调整回右侧

### 4.WPS卡顿，主要是幻灯片放映，尤其是演讲者模式

### 5.vim的hjkl

### 6.扩展屏

show applications

### 7.待机界面时间的秒数显示

### 8.两种md文件

### 9.同一wifi下 zero-tier不能ssh连接的问题

### 10.公网IP

Linux 下获取当前操作系统的广域网IP地址而不是NAT下的地址命令：curl getip.name

局域网下部署的web服务怎么公网访问？ 花生壳内网穿透？

```
2: enp3s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc fq_codel state DOWN group default qlen 1000
    link/ether 54:ee:75:ac:0e:e6 brd ff:ff:ff:ff:ff:ff
3: wlp2s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc noqueue state UP group default qlen 1000
    link/ether 68:07:15:4e:6f:ce brd ff:ff:ff:ff:ff:ff
    inet 10.162.189.37/16 brd 10.162.255.255 scope global dynamic noprefixroute wlp2s0
       valid_lft 11260sec preferred_lft 11260sec
    inet6 2403:d400:1001:2:5b98:9e20:c133:fd20/64 scope global dynamic noprefixroute 
       valid_lft 86397sec preferred_lft 14397sec
    inet6 fe80::aad2:1203:d5f8:2e04/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever

```

无线网卡 和 有线网卡

通过有限网卡mac地址 申请 校园网开网，获得公网ip，直接部署web服务？这个过程数据流量怎么运转，要不要经过网络信息中心？

无线网卡 分为 两类？可以直接上网的，和内置的一般的内网无线网卡？

无线网卡 申请到 公网ip有用么？

希望ssh访问我的笔记本电脑，有几种可操作的方式？ 笔记本插网线变成台式机？或者保留他无线的形式可行？

### 11.锁屏界面到输入密码界面卡顿

218.193.183.88

218.193.183.83



### 12.第一个大问题 [manjaro error: file '/boot/vmlinuz-5.7-x86_64' not found]

1.windows + rufus 制作 manjaro 启动盘

注意 rufus [版本](https://rufus.ie/)，新版本可能无法修改MBR/GPT，以及 uefi 。 选择3.4即可。 后续弹窗选择DD

manjaro镜像可以从官网，清华园，中科大源下载。[link](https://manjaro.org.cn/category/download-manjaro)

2.进入bios，u盘启动

3.进入terminal

[参考](https://blog.csdn.net/AI_Fanatic/article/details/105109663)

[参考2](https://www.cnblogs.com/Observer-A/p/13695282.html)

```
su  #切换root
sudo pacman-mirrors -i -c China -m rank #换个国内源

# 查看你原来那个系统硬盘root分区的设备文件名，例如/dev/sdb2
sudo fdisk -l
# 这里换成上一步你自己查到的设备名
sudo mount -t ext4 /dev/sdb2 /mnt

sudo pacman -Sy arch-install-scripts
# 一定是arch-chroot
arch-chroot /mnt
sudo pacman -Sy linux
exit
reboot 
```

区别

文件系统为lvm

需要

```
sudo pacman -Sy lvm2
lvdisplay

sudo mount /dev/vg1/lvol_root
```



### 13.双系统时间同步

问题原因: **windows 将 主板上的硬件时间直接拿来当作北京时间，而manjaro将主板上的硬件时间当作UTC时间（0时区时间）**

**windows 开机直接把时间拿来用了，自动同步不及时，换到manjaro，开机时联网更新时间，发现主板上的时间不对，就立刻修改为UTC，这样在进入windows时间出了问题。**

电脑系统中有两个时间：

- 硬件时间：保存在主板中，信息比较少没时区、夏令时的概念
- 系统时间：又系统维护，独立于硬件时间，拥有时区、夏令时等信息

系统时间又因为系统的不同使用了两种时间管理办法：

- localtime：本地时间，目前只有 Windows 在使用。
- UTC：是一种世界标准时间，Linux 这类类 UNIX 多数会使用，UTC 加减时区之后才是本地时间。

然后问题就来了
Windows 认为硬件时间就是本地时间，所以会直接把主板中的时间拿来当做当前的时间。设置或同步时间后也会把“正确”的时间写入主板。

而 Linux 认为硬件时间是 UTC 标准时间，Linux 时间同步后会把“正确”的时间 -8 之后作为标准 UTC 标准时间写入主板。

而貌似 Linux 启动时就会链接网络同步时间，所以硬件时间很迅速的就被替换为了 UTC 。但是 Windows 比较懒，虽然我们都开启了自动同步时间，但是往往不是很及时，所以错把为 +8 的 UTC 时间当做了正确的显示了出来。

#### 让 Windows 使用 UTC

这需要修改注册表，而且不能开启时间同步，以免我们的设置被重置。由于我的 Windows 是主力系统，因此没有尝试下面的方法，有效性有待验证

```
# 以管理员身份使用运行
reg add "HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\TimeZoneInformation" /v RealTimeIsUniversal /d 1 /t REG_DWORD /f

# 以上方法无效或64位系统：
reg add "HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\TimeZoneInformation" /v RealTimeIsUniversal /d 1 /t REG_QWORD /f12345
```

#### 让 Linux 使用本地时间

委屈以下 Linux 吧，Manjaro 或 Arch 可以在终端中输入：

```
sudo timedatectl set-local-rtc true
```



### 14.一些新的问题

关于zsh划分窗口

vim常用操作

zsh快捷指令

zsh字体调整  Ctrl + -(主键区)  Crrl++（主键区）

桌面新建

历史记录

4.17 vim细节操作 ALT+tab切应用，那怎么在两个terminal之间切换？

常用的 文本处理 grep 。。。。

4.25 平铺有没有必要 vim和剪切板交互



### 15.

~~~
# 查看盘符等信息
sudo fdisk -l
# 假设U盘对应的盘符为 /dev/sdc
 
# 先卸载U盘
# 加*是因为：U盘存在多个分区，比如sdc1, sdc2
sudo umount /dev/sdc*
 
# 格式U盘为FAT格式
# 常见Linux的ISO文件没有超过的4G的，所以可以选择FAT格式。
# -I：如果U盘存在多个分区，就需要这个参数强行抹除，不加这个参数会失败；
sudo mkfs.vfat /dev/sdc -I
 
# 直接写入镜像
# 上一步使用了-I参数，U盘上已经没有任何分区了，所以of=/dev/sdc，没有数字
# status=progress可以显示进度
sudo dd if=xx.iso of=/dev/sdc bs=4M status=progress
~~~

