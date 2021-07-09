

## git又学到了

#### 1.main master

#### 2.操作

对于已经有了的很多代码，突然想提交到git，怎么操作。

首先，去github创建仓库，然后，来到项目文件夹下，

~~~
git init
git remote add origin git@github.com:Twang1998/NRsvr.git

git add .
git commit -m 'test'
git pull origin main  ##先pull一下，可以的
git push origin main
~~~

应该就可以了。

今天在操作的时候犯了个错误，最后一句指令写成了

~~~
git push origin master
~~~

这会导致一个问题，创建 master 分支，然后把东西都push到新的分支上，接下来要开始解决这个问题。

首先，我们需要把这些东西搞到 main 上，

~~~
git branch  ##查看当前所在分支。
git branch -a ##查看所有分支，包括远程分支

git checkout main  ##切换到main分支
git merge master ##merge master分支内容到 mian (本地分支操作)
git push origin main ##刷新main

##打算删除分支
git branch -d master ##删除本地分支
git push origin --delete master ##删除远程分支

##结束
~~~

#### 3.这样开始也可以(从零开始)

~~~
echo "# simtest" >> README.md
git init
git add README.md
git commit -m "first commit"
git branch -M main  ##重命名 强制。有啥用？
git remote add origin git@github.com:Twang1998/simtest.git
git push -u origin main
~~~

ok ,强制重命名是有用的。

~~~
git init
git branch  ##无输出

git add similar.py
git commit -m '0'
git branch  ##输出 master

git branch -M main ##作用来了，要改名。

git remote add origin git@github.com:Twang1998/simtest.git
git pull origin main
git push -u origin main
~~~



### 4.git API

如何在命令行新建GitHub远程仓库？

[参考连接](https://my.oschina.net/eduOSS/blog/287824)

- 新建API token。

setting  -> developer settings   -> personal access tokens

- ~~~
  curl -u "$username:$token" https://api.github.com/user/repos -d '{"name":"'$repo_name'"}'
  ~~~

- ~~~
  github-create() {
    repo_name=$1
   
    dir_name=`basename $(pwd)`
   
    if [ "$repo_name" = "" ]; then
      echo "Repo name (hit enter to use '$dir_name')?"
      read repo_name
    fi
   
    if [ "$repo_name" = "" ]; then
      repo_name=$dir_name
    fi
   
    username=`git config github.user`
    if [ "$username" = "" ]; then
      echo "Could not find username, run 'git config --global github.user <username>'"
      invalid_credentials=1
    fi
   
    token=`git config github.token`
    if [ "$token" = "" ]; then
      echo "Could not find token, run 'git config --global github.token <token>'"
      invalid_credentials=1
    fi
   
    if [ "$invalid_credentials" == "1" ]; then
      return 1
    fi
   
    echo -n "Creating Github repository '$repo_name' ..."
    curl -u "$username:$token" https://api.github.com/user/repos -d '{"name":"'$repo_name'"}' > /dev/null 2>&1
    echo " done."
   
    echo -n "Pushing local code to remote ..."
    git remote add origin git@github.com:$username/$repo_name.git > /dev/null 2>&1
    git push -u origin master > /dev/null 2>&1
    echo " done."
  }
  ~~~

- ~~~
  github-create() 
  {if [ $1 ]
  then
      repo_name=$1
  else
      echo "Repo name?"
      read repo_name
  fi 
  curl -u '$username:$token' https://api.github.com/user/repos -d '{"name":"'$repo_name'"}'
  git remote add origin git@github.com:efatsi/$repo_name.git
  git push -u origin master
  }
  ~~~

  ~~~
  Source  ~/.bash_profile
  source ~/zshrc_custom
  ~~~

~~~
git config user.name=''
git config user.email=''
git config github.token=''
~~~



通过 SSH 协议克隆版本库，你可以指定一个 ssh:// 的 URL：
 git clone ssh://[user@]server/project.git
或者使用一个简短的 scp 式的写法：
​git clone [user@]server:project.git



由于在现代的 Linux 发行版中，systemd 是最常见的初始化系统，因此你可以用它来达到此目的。 只要在
/etc/systemd/system/git-daemon.service 中放一个文件即可，其内容如下：
[Unit]
Description=Start Git Daemon
[Service]
ExecStart=/usr/bin/git daemon --reuseaddr --base-path=/srv/git/ /srv/git/
Restart=always
RestartSec=500ms
StandardOutput=syslog
StandardError=syslog
SyslogIdentifier=git-daemon
User=git
Group=git
[Install]
WantedBy=multi-user.target

最后，你需要运行 systemctl enable git-daemon 以让它在系统启动时自动运行， 这样也能让它通过
systemctl start git-daemon 启动，通过 systemctl stop git-daemon 停止。



### [添加gitignore文件后使其生效](https://www.cnblogs.com/AliliWl/p/7880243.html)

```none
git rm -r --cached . // 删除本地缓存
git add . // 添加要提交的文件
git commit -m 'update .gitignore' // 更新本地的缓存
```