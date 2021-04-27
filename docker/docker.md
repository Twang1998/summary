## Docker

### 1.非root用户

> [official](https://docs.docker.com/engine/install/linux-postinstall/)

~~~
sudo cat /etc/group | grep docker ##look whether there is a docker group
sudo groupadd docker  ## if not, add a group docker
sudo usermod -aG docker $USER  ## add user in docker group
sudo systemctl restart docker ## restart
~~~

>now maybe you do not have permission of /var/run/docker.sock, please reboot your system. 

~~~
> ll /var/run/docker.sock
srw-rw---- 1 root docker 0 Apr 27 13:40 /var/run/docker.sock

sudo chmod a+rw /var/run/docker.sock  ##nop!!!
~~~

> I do not think above command is right ,  why should add user to docker group? because docker group has the permission of the .sock file. if we chmod a+rw, actually we need not add user to docker group.

