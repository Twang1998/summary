### git（windows）

参考：https://blog.csdn.net/u014103733/article/details/79190004

1.安装git，没啥好说的

2.配置一下用户名，邮箱

```
git config--global user.name "your_account"

git config –globaluser.email youremail@example.com
```

3.生成SSH

```
$ ssh-keygen -t rsa -C  371515509@qq.com
Generating public/private rsa key pair.
Enter file in which to save the key (/c/Users/37151/.ssh/id_rsa):
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in /c/Users/37151/.ssh/id_rsa.
Your public key has been saved in /c/Users/37151/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:cCDnlgva340pnFpZ6y78Y9HjBtsobzstyjSm7FKO3nA 371515509@qq.com
The key's randomart image is:
+---[RSA 3072]----+
|    . o          |
|     + o         |
|    . = .        |
|   o o +         |
|  . . . S.       |
|    .o =o=o      |
|  .+E.@ =O..     |
|  o=.B++O =      |
| ..o* oX**       |
+----[SHA256]-----+
```

4.github添加

没啥好说的，title随意

4.5   

5.可以git clone 了

clone 自动绑定远程仓库，接下来可以搞事了

```
$git add .
git commit -m "first commit"
git push origin master
```

问题不大

6.不clone的话

从初始化仓库开始

https://www.jianshu.com/p/8e46d88db49e

①初始化本地仓库

```undefined
git init
```

②将所有文件添加到本地仓库（add 后面的空格+点 不能少）

```csharp
git add .
```

③将项目提交到本地git仓库 （“first commit” 是备注信息 自己随便写）

```bash
git commit -m "first commit"
```

④本地git仓库与远程仓库关联（git@[xx.xx.xx.xx:repos/xxx/xxx/xxx.git](https://links.jianshu.com/go?to=xx.xx.xx.xx%3Arepos%2Fxxx%2Fxxx%2Fxxx.git) 是远程仓库地址）

```csharp
git remote add origin git@xx.xx.xx.xx:repos/xxx/xxx/xxx.git
```

⑤将项目推送到远程仓库(master是分支名 -f 强制推送)

```undefined
git push -u origin master -f 或者 git push origin master

git push -u origin master
```

执行⑤出错的话 执行下面命令后 在执行⑤

```undefined
git pull --rebase origin master
```

⑥强拉失败 执行如下命令

```gi
git pull origin master --allow-unrelated-histories
```



ssh-add ~./.ssh/id_rsa

git remote rm origin

git remote add urlcopy

echo *** >>.gitignore

ssh -T git@github.com 

**远程仓库**

[https://git-scm.com/book/zh/v1/Git-%E5%9F%BA%E7%A1%80-%E8%BF%9C%E7%A8%8B%E4%BB%93%E5%BA%93%E7%9A%84%E4%BD%BF%E7%94%A8](https://git-scm.com/book/zh/v1/Git-基础-远程仓库的使用)

### [查看当前的远程库](https://git-scm.com/book/zh/v1/Git-基础-远程仓库的使用#查看当前的远程库)

要查看当前配置有哪些远程仓库，可以用 `git remote` 命令，它会列出每个远程库的简短名字。在克隆完某个项目后，至少可以看到一个名为**origin 的远程库**，Git 默认使用这个名字来标识你所克隆的原始仓库：

```
$ git clone git://github.com/schacon/ticgit.git
Cloning into 'ticgit'...
remote: Reusing existing pack: 1857, done.
remote: Total 1857 (delta 0), reused 0 (delta 0)
Receiving objects: 100% (1857/1857), 374.35 KiB | 193.00 KiB/s, done.
Resolving deltas: 100% (772/772), done.
Checking connectivity... done.
$ cd ticgit
$ git remote
origin
```

也可以加上 `-v` 选项（译注：此为 `--verbose` 的简写，取首字母），显示对应的克隆地址：

```
$ git remote -v
origin  git://github.com/schacon/ticgit.git (fetch)
origin  git://github.com/schacon/ticgit.git (push)
```

如果有多个远程仓库，此命令将全部列出。比如在我的 Grit 项目中，可以看到：

```
$ cd grit
$ git remote -v
bakkdoor  git://github.com/bakkdoor/grit.git
cho45     git://github.com/cho45/grit.git
defunkt   git://github.com/defunkt/grit.git
koke      git://github.com/koke/grit.git
origin    git@github.com:mojombo/grit.git
```

这样一来，我就可以非常轻松地从这些用户的仓库中，拉取他们的提交到本地。请注意，上面列出的地址只有 origin 用的是 SSH URL 链接，所以也只有这个仓库我能推送数据上去（我们会在第四章解释原因）。

### [添加远程仓库](https://git-scm.com/book/zh/v1/Git-基础-远程仓库的使用#添加远程仓库)

要添加一个新的远程仓库，可以指定一个简单的名字，以便将来引用，运行 `git remote add [shortname] [url]`：

```
$ git remote
origin
$ git remote add pb git://github.com/paulboone/ticgit.git
$ git remote -v
origin  git://github.com/schacon/ticgit.git
pb  git://github.com/paulboone/ticgit.git
```

现在可以用字符串 `pb` 指代对应的仓库地址了。





https://git-scm.com/book/zh/v1/%E8%B5%B7%E6%AD%A5  牛批