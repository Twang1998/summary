### conda

 conda create -n tensorflow python=3.5

### conda pip

> 进入虚拟环境后，尽量使用conda装包，但是pip的包更全面丰富
>
> 使用pip要注意使用的是哪一个pip

> `echo $PATH`可以知道为什么有些时候会是你不想要的那个pip

~~~shell
which pip
which -a pip
where pip
~~~

一般情况下，进入虚拟环境后，会默认选择虚拟环境中的pip

>一次pip更新后出了问题。

~~~shell
curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py
python get-pip.py
虚拟环境中执行，解决问题。
~~~

> 进一步探索

登陆shell时会加载很多脚本，bash检查环境变量文件的情况取决于系统运行shell的方式。[link](https://blog.51cto.com/zpf666/2334770)

`.bashrc`,`.profile`,`.bash_profile`

`.profile`里有这么一句

` PATH="$HOME/bin:$HOME/.local/bin:$PATH"`

```shell
(base) wangtao@gdp-SYS-7049GP-TRT:~$ echo $PATH
/usr/local/cuda-10.0/bin:/home/wangtao/.vscode-server/bin/2b9aebd5354a3629c3aba0a5f5df49f43d6689f8/bin:/home/wangtao/bin:/home/wangtao/.local/bin:/home/gdp/anaconda3/bin:/home/gdp/anaconda3/condabin:/usr/local/cuda-10.0/bin:/home/wangtao/.vscode-server/bin/2b9aebd5354a3629c3aba0a5f5df49f43d6689f8/bin:/home/wangtao/bin:/home/wangtao/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
(base) wangtao@gdp-SYS-7049GP-TRT:~$ conda activate pytorch
(pytorch) wangtao@gdp-SYS-7049GP-TRT:~$ echo $PATH
/usr/local/cuda-10.0/bin:/home/wangtao/.vscode-server/bin/2b9aebd5354a3629c3aba0a5f5df49f43d6689f8/bin:/home/wangtao/bin:/home/wangtao/.local/bin:/home/wangtao/.conda/envs/pytorch/bin:/home/gdp/anaconda3/condabin:/usr/local/cuda-10.0/bin:/home/wangtao/.vscode-server/bin/2b9aebd5354a3629c3aba0a5f5df49f43d6689f8/bin:/home/wangtao/bin:/home/wangtao/.local/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/usr/local/games:/snap/bin
```

