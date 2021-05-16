## Linux passwd
### Forget passwd

[ref](https://itsfoss.com/how-to-hack-ubuntu-password/)

通过一定的手段获得root权限，以及文件的读写权限

> 例如，grub界面选择 `advanced options for manjaro`，进入`recovery mode`，选择`root Drop to the root shell prompt`，然后`mount -rw -o remount /`

> 或者 grub 界面，按`E`进入编辑grub模式，
>
> Find the line starting with ‘linux’, change the **ro** to **rw** and append **init=/bin/bash** at the end of that line.

```
ls /home
passwd user
```

