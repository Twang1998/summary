## what I do

### 0. sudo

~~~
sudo vim /etc/sudoers.d/twang
### add 
### twang ALL=(ALL) NOPASSWD:ALL
### or append to the file /etc/sudoers
~~~

### 0. desktop icon

~~~
extension desktop icon ng
~~~



### 1. browser

~~~
yay -S google-chrome
sudo pacman -R firefox firefox-gnome-theme-maia
~~~

### 2. ifconfig

~~~
sudo pacman -S net-tools
~~~

### 3. zero-tier one

~~~
sudo pacman -S zerotier-one
sudo zerotier-one -d   ###It is important
sudo zerotier-cli join e5cd7a9e1c700789
sudo systemctl list-unit-files --type=service | grep zerotier
sudo systemctl enable zerotier-one.service
~~~

~~~
ssh tw@10.242.36.193  ##test
ssh-keygen 
ssh-copy-id tw@10.242.36.193
scp tw@10.242.36.193:.ssh/config .ssh/    ##need some change
scp tw@10.242.36.193:.gitconfig .
~~~

### 4. clash

~~~shell
sudo pacman -S clash
cd .config/clash
mv config.yaml config.yaml.bkup
wget -O config.yaml https://s.trojanflare.com/clashx/80251f48-b43e-43d0-ba90-e681366a6023
mv Country.mmdb Country.mmdb.bkup
scp tw@10.242.36.193:.config/clash/Country.mmdb .
#### http://clash.razord.top/

sudo systemctl list-unit-files --type=service | grep clash
sudo systemctl start clash@twang.service
sudo systemctl enable clash@twang.service
~~~

now we cannot use google, we should set proxy

~~~
setting -> network -> network proxy
~~~

<img src="what I do/image-20210326144823020.png" alt="image-20210326144823020" style="zoom: 67%;" />

then config the swithomega, just copy the bakeup link. The we can turn off the proxy and use google.

### 5. .dotfiles

~~~
git clone https://github.com/spartazhc/dotfiles.git .dotfiles
cd .dotfiles
git clone https://github.com/anishathalye/dotbot.git dotbot
./install

### restart zsh, need adding some plugins, now we should open the proxy because git sometimes do not work.

sudo pacman -S xcape

### xcape service doesnot exist. 
~~~

### 6. some software

~~~
yay -S visual-studio-code-bin
yay -S wps-office
yay -S ttf-wps-fonts
yay -S typora
yay -S nutstore
~~~

### 7. fcitx

~~~
sudo pacman -S fcitx-im fcitx-configtool fcitx-cloudpinyin
sudo vim .xprofile
### add
### export GTK_IM_MODULE=fcitx
### export QT_IM_MODULE=fcitx
### export XMODIFIERS="@im=fcitx"
### need to restart
~~~

