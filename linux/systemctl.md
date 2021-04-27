## systemctl

### 1.user

[ref](https://www.cnblogs.com/hadex/p/6571278.html)

> **systemd 支持普通用户定义的 unit[s] 开机启动**
>
> systemctl --user enable/disable/start/stop/daemon-reload... xxx.timer/xxx.service...
>
> --user 不可省略，因为默认是执行 systemctl [--system]，对于系统级 unit[s] 来说，不必显式添加 --system 选项

**用户自定义的 unit[s] 可以放置在如下四个位置**

- /usr/lib/systemd/user：优先级最低，会被高优先级的同名 unit 覆盖
- ~/.local/share/systemd/user
- /etc/systemd/user：全局共享的用户级 unit[s]
- ~/.config/systemd/user：优先级最高

**注：**

1. 用户级 unit 与系统级 unit 相互独立，不能互相关联或依赖
2. 用户级 unit 运行环境用 default.target，系统级通常用 multi-user.target
3. 即使用户不登陆，其定制的服务依然会启动

[教程](http://www.ruanyifeng.com/blog/2016/03/systemd-tutorial-commands.html)