### python virtualenv

```
sudo pip install virtualenv
sudo pip install virtualenvwrapper
```

进入 用户主目录，打开 *.bashrc* 文件，添加如下代码：

```bash
#export WORKON_HOME=$HOME/.virtualenvs
#export PROJECT_HOME=$HOME/Devel
#source /usr/local/bin/virtualenvwrapper.sh

export WORKON_HOME='~/.virtualenvs'
export VIRTUALENVWRAPPER_PYTHON="/usr/bin/python3" 
source /usr/bin/virtualenvwrapper.sh
```

~~~
$ source .bashrc
~~~

**workon:**                                    列出虚拟环境列表
**lsvirtualenv**        详细的列出我们创建的虚拟环境
**mkvirtualenv [虚拟环境名称]:**        新建虚拟环境
**workon [虚拟环境名称]:**            切换虚拟环境
**rmvirtualenv [虚拟环境名称]:**    删除虚拟环境
**deactivate:**                                离开虚拟环境
**showvirtualenv  [虚拟环境名称]**