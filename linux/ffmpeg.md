## ffmpeg

### ffmpeg 批量抽帧

> 对于YUV格式文件，要指定分辨率 `-s`

~~~bash
#!/usr/bin/env bash

videos_root=OriginalYUV
save_root=CSIQ_VQA_Images/
for video in $videos_root/*;
do
    echo $video
    save_dir=$save_root$(basename $video .yuv)
    if [ ! -d $save_dir ]; then
        mkdir $save_dir
    fi
    ~/ffmpeg/ffmpeg-git-20210501-amd64-static/ffmpeg -s 832x480 -i $video -r 1 -q:v 2 -f image2 $save_dir/%03d.png
done
~~~

### 个人安装ffmpeg

[ref](https://blog.csdn.net/u013314786/article/details/89682800)

- https://johnvansickle.com/ffmpeg/
- git master built & wget link

~~~
wget https://johnvansickle.com/ffmpeg/builds/ffmpeg-git-amd64-static.tar.xz
~~~

- xz -d
- tar -xvf
- 得到可执行文件

