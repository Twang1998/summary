## manjaro

```
nvidia-smi
sudo pacman -S archlinuxcn-keyring
sudo pacman -S fcitx-im
sudo pacman -S fcitx-im fcitx-configtool fcitx-sunpinyin fcitx-cloudpinyin
sudo vim .xprofile
sudo pacman -Ss vim
sudo pacman -Syu
sudo pacman -S vim
yay -Syu
yay -S google-chrome
yay -Ss vscode
yay -Ss visual-studio-code
yay -Ss visual-studio-code-bin
yay -Si visual-studio-code-bin
yay -S visual-studio-code-bin
yay -Qs visual-studio-code-bin
yay -Qi visual-studio-code-bin
yay -QL visual-studio-code-bin
yay -Ql visual-studio-code-bin
sudo pacman R firefox
sudo pacman -R firefox
sudo pacman -R firefox firefox-gnome-theme-maia
sudo grub-update
blkid
sudo blkid
lsblk
sudo mount /dev/nvme0n1p5 /mnt
cd /mnt
cd System\ Volume\ Information
cd ..
sudo umount /mnt
sudo pacman -Ss boot-repair
sudo update-grub
sudo reboot
sudo pacman -Ss tpm
sudo pacman -Ss tmux-pl
yay -S tpm
yay -Si tpm
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
tmux
sudo pacman -Ss vim-plug
sudo pacman -S vim-plug
vim .vimrc
vim
sudo pacman -Qs cmake
sudo pacman -S base-devel
sudo pacman -S cmake git
git clone https://github.com/spartazhc/dotfiles .dotfiles
sudo pacman -Ss tmux
sudo pacman -S tmux
./install_dotfiles.sh
cat install_plugins.sh
sudo pacman -S mpv
ls --color
sudo vim /usr/share/zsh/manjaro-zsh-config
cat .zshrc
sudo vim /usr/share/zsh/manjaro-zsh-prompt
vim .zshrc_custom
cd .dotfiles
sudo pacman -Ss typora
yay -Ss trojan
yay -Si trojan
yay -S trojan
sudo pacman -S typora
sudo ./torjan
sudo ./trojan
trojan
yay -Ss wechat
yay -S electronic-wechat-bin
cd /tmp
wget https://s.trojanflare.com/subscription/shadowrocket/80251f48-b43e-43d0-ba90-e681366a6023
vim 80251f48-b43e-43d0-ba90-e681366a6023
wget https://s.trojanflare.com/subscription/shadowrocket/80251f48-b43e-43d0-ba90-e681366a6023 config.json
killall trojan
mkdir clash
wget https://s.trojanflare.com/clashx/80251f48-b43e-43d0-ba90-e681366a6023 -O config.yaml
clash -h
scp spartazhc@homeofspartazhc.tpddns.cn:.config/clash/
scp spartazhc@homeofspartazhc.tpddns.cn:.config/clash/mmdb
scp spartazhc@homeofspartazhc.tpddns.cn:.config/clash/Country.mmdb
scp spartazhc@homeofspartazhc.tpddns.cn:.config/clash/Country.mmdb .
vim config.yaml
clash -d /home/tw/.config/clash
sudo systemctl enable clash@tw.service
sudo systemctl start clash@tw.service
sudo trojan
curl https://s.trojanflare.com/clashx/80251f48-b43e-43d0-ba90-e681366a6023
sudo pacman -S clash
trojan -h
sudo vim /etc/trojan/config.json
sudo trojan &
pkill -f trojan
sudo pkill -f trojan
sudo trojan 
ps -ef |grep trojan
mv 80251f48-b43e-43d0-ba90-e681366a6023 config.json
sudo trojan  -c config.json
curl https://s.trojanflare.com/subscription/shadowrocket/80251f48-b43e-43d0-ba90-e681366a6023
curl trojan://uMJpcqzrKjwjQvb5S7@fm1-3.sstr-api.xyz:443
sudo pacman -R trojan
yay -S activitywatch-bin
cd .config
cd clash
clash
sudo pacman -Ss wps
sudo pacman -S wps-office
sudo shutdown now
```



### 1.输入法

```
sudo pacman -S fcitx-im fcitx-configtool fcitx-sunpinyin fcitx-cloudpinyin
sudo vim .xprofile
```

```
export GTK_IM_MODULE=fcitx                                                 
export QT_IM_MODULE=fcitx
export XMODIFIERS=”@im=fcitx”
```

### 2.装软件

```
sudo pacman -Ss vim
sudo pacman -Syu
sudo pacman -S vim
yay -Syu
yay -S google-chrome
yay -Ss vscode
yay -Ss visual-studio-code
yay -Ss visual-studio-code-bin
yay -Si visual-studio-code-bin
yay -S visual-studio-code-bin
yay -Qs visual-studio-code-bin
yay -Qi visual-studio-code-bin
yay -QL visual-studio-code-bin  #problem 
yay -Ql visual-studio-code-bin
sudo pacman R firefox
sudo pacman -R firefox
sudo pacman -R firefox firefox-gnome-theme-maia
```

### 3.服务

```
systemctl enable sshd.service 开机启动
systemctl start sshd.service 立即启动
systemctl restart sshd.service 立即重启
systemctl enable servicename;设置为开机启动;
systemctl disable servicename;禁止开机启动;

pacman -Ql zerotier-one
zerotier-one /usr/lib/systemd/system/zerotier-one.service

systemctl list-unit-files --type=service |grep clash              
clash@.service                             indirect        disabled

ystemctl list-unit-files --type=service |grep zerotier           
zerotier-one.service                       enabled         disabled

systemctl is-enabled clash.service  
Failed to get unit file state for clash.service: No such file or directory

systemctl is-enabled clash@.service                    
indirect

```

### 4.curl & wget

```
curl -O http://man.linuxde.net/text.iso               #O大写，不用O只是打印内容不会下载
wget http://www.linuxde.net/text.iso                  #不用参数，直接下载文件

curl -o rename.iso http://man.linuxde.net/text.iso         #o小写
wget -O rename.zip http://www.linuxde.net/text.iso         #O大写
```

### 5.常用命令

[参考](https://my.oschina.net/u/4172591/blog/3190284)

```
输出系统基本信息:sudo screenfetch
强制关机:sudo shutdown now
升级系统:sudo pacman -Syyu
清理系统中无用的包:sudo pacman -R $(pacman -Qdtq)
清除已下载的安装包:sudo pacman -Scc
显示文件系统的磁盘使用情况:sudo df -h或sudo df -hT
显示文件系统的磁盘使用情况:sudo fdisk -u -l
```

```
安装应用 sudo pacman -S '应用名'
删除应用 sudo pacman -R '应用名'
升级应用 sudo pacman -Syu '应用名'

pacman -Ss abc                   搜索有关abc信息的包
pacman -Si abc                    从数据库中搜索包abc的信息
pacman -R abc                     删除abc包
pacman -Rc abc                   删除abc包和依赖abc的包

pacman -Q                           列出系统中所有的包
pacman -Q package             在本地包数据库搜索(查询)指定软件包
pacman -Qi package            在本地包数据库搜索(查询)指定软件包并列出相关信息

pacman -U    安装本地包
pacman -Sw    下载但不安装
```

```
1、添加新账户
useradd username新建账户;
useradd -d /home/xxx -m xxx创建用户，并同时生成用户目录，不然账户无法正常启用;
passwd username修改密码;
userdel -f username删除账户及其配置文件;
usermod -G gpname usrname修改用户所属组;
```

```
yay安装好后，应该可以使用了，请注意，你不需要使用sudo权限

yay -S package   使用yay从AUR安装软件包
yay -Rns package   删除包
yay -Syu 升级所有已安装的包

yay -Yc   删除系统上所有不需要的依赖项

搜索：
yay -Ss
安装：
yay -S
删除：
yay  -Rns
使用yay打印系统统计信息:
yay -Ps
检查安装的版本：
yay -Qi
清理不需要的依赖:
yay -Yc
更新
yay -Syu
```

### 6.sudo

可以通过修改 /etc/sudoers 文件 或者 将配置文件添加到 /etc/sudoers.d 目录来配置用户访问权限

1.在/etc/sudoers 文件末尾追加 tw ALL=(ALL) NOPASSWD:ALL

2.

```
sudo nano /etc/sudoers.d/tw   #文件最好以用户名命名
文件内只要上边那一句话，保存并退出即可。
```

### 7.桌面图标

插件 desktop icon ng 控制



### 8.hexo

node 版本问题，太高不行

sudo pacman -S nodejs-lts-erbium      ##fermium不行

hexo5 删除插件，需要自己安装

npm i hexo-renderer-swig  

hexo空文件夹 hexo init 直接删除最开始创建的文件夹下的一些东西，可能有nodemodule文件夹或者某个json文件，直接删除，然后init，

把备份内容复制 ，主题，文章，等内容



### 9.pacman

~~~
(base) ~ >>> sudo pacman -h                                                    
usage:  pacman <operation> [...]
operations:
    pacman {-h --help}
    pacman {-V --version}
    pacman {-D --database} <options> <package(s)>
    pacman {-F --files}    [options] [package(s)]
    pacman {-Q --query}    [options] [package(s)]
    pacman {-R --remove}   [options] <package(s)>
    pacman {-S --sync}     [options] [package(s)]
    pacman {-T --deptest}  [options] [package(s)]
    pacman {-U --upgrade}  [options] <file(s)>

use 'pacman {-h --help}' with an operation for available options
~~~

1、列出已经安装的软件包

```
pacman -Q
```

2、查看sqlmap包是否已经安装

```
pacman -Q sqlmap
```

3、查看已安装的包sqlmap的详细信息

```
pacman -Qi sqlmap
```

4、列出已安装包sqlmap的所有文件

```
pacman -Ql sqlmap
```

5、查找某个文件属于哪个包？

```
pacman -Qo /etc/passwd
```

6、查询包组

```
pacman -Sg 
```

7、查询包组所包含的软件包

```
pacman -Sg blackarch
```

8、搜索sqlmap相关的包

```
pacman -Ss sqlmap
```

9、从数据库中搜索sqlmap的信息

```
pacman -Si sqlmap
```

10、仅同步源

```
sudo pacman -Sy
```

10、更新系统

```
sudo pacman -Su
```

11、同步源并更新系统

```
sudo pacman -Syu 
```

12、同步源后安装sqlmap包

```
sudo pacman -Sy sqlmap
```

13、从本地数据库中获取sqlmap的信息，并下载安装

```
sudo pacman -S sqlmap
```

14、强制安装sqlmap包

```
sudo pacman -Sf sqlmap
```

 15、删除sqlmap

```
sudo pacman -R sqlmap
```

 16、强制删除被依赖的包（慎用）

```
sudo pacman -Rd sqlmap
```

 17、删除sqlmap包及依赖其的包

```
sudo pacman -Rc sqlmap
```

 18、删除sqlmap包及其依赖的包

```
sudo pacman -Rsc sqlmap
```

 19、清理/var/cache/pacman/pkg目录下的旧包

```
sudo pacman -Sc
```

 20、清除所有下载的包和数据库

```
sudo pacman -Scc
```

 21、安装下载的virtualbox包（有时候需要降级包的时候就用这个）

```
cd /var/cache/pacman/pkgsudo
pacman -U virtualbox-5.2.12-1-x86_64.pkg.tar.xz
```

 22、升级时不升级sqlmap包

```
sudo pacman -Su --ignore sqlmap
```

```
update-grub
sudo update-grub
su
lsblk
sudo os-prober
ls
sudo vim /etc/grub.d/40_custom
grub-probe --target=fs_uuid /boot/EFI/Microsoft/Boot/bootmgfw.efi
sudo grub-probe --target=fs_uuid /boot/EFI/Microsoft/Boot/bootmgfw.efi
sudo grub-probe --target=fs_uuid /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
ls
lsblk
ls
sudo os-prober
ls /mnt
sudo mount /dev/nvme0n1p2 /mnt
cd /mnt
ls
cd EFI
ls
cd Microsoft
ls
cd ..
ls
sudo cp -r Microsoft /boot/efi/EFI/
ls
sudo grub-probe --target=fs_uuid /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
sudo grub-probe --target=hints_string /boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
sudo vim /boot/grub/grub.cfg
sudo os-prober
\
sudo grub-mkconfig -o /boot/grub/grub.cfg
sudo update-grub
sudo vim /etc/grub.d/40_custom
sudo update-grub
sudo reboot
mkdir .dist

```

```

/boot/grub/grub.cfg


(base) ~ >>> ls /etc/grub.d                                                    
00_header  20_linux_xen  30_uefi-firmware  41_custom	  README
10_linux   30_os-prober  40_custom	   60_memtest86+


/etc/default/grub   ##这个修改会update到上一个 sudo update-grub   ##一些属性配置，某某属性 = true false
### GRUB_DISABLE_OS_PROBER=false
### GRUB_TIMEOUT_STYLE=menu
/etc/grub.d/40_custom  并列多个启动项文件

这两个都会体现在最上边那个里
```

上图中有一个40_custom的脚本: 可以通过修改40_custom脚本来加入自定义的启动项.