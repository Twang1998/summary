## shell script

### ffmpeg 批量抽帧

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

### 批量解压缩

~~~bash
#!/bin/bash
cd /data/limiao/develop_data/AISHELL-2/iOS/data/wav
# 首先把要解压的文件（tar.gz格式）放入一个文件中
ls *.tar.gz>ls.log
# 这样就会把所有的文件名保存到ls.log文件中
for i in $(cat ls.log)   # 这里可以使用Linux命令cat
do
   tar -zxf $i & > /dev/null   #  & > /dev/null语句的意思是让输出的东西不要显示出来
done
~~~

