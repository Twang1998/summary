## Computer Network

### 1. 查询公网ip

> 一段比较曲折的经历

> **ipconfig / ifconfig**
>
> 可以获得 内网ip，子网掩码，默认网关

> **pathping** 
>
> 结合了 tracert & ping
>
> 可以获得和某ip/域名建立联接时的路径。使用ICMP回应信息来分析网络的联通情况，返回两部分内容，分别是到达目的地经过的所有路由以及每个路由上数据包丢失情况。
>
> \# linux 系统类似工具 **mtr**
>
> 结果，无法得到需要的公网ip，一级网关标识的内网ip，无法获得对应的外网ip。

> **ip.cn**
>
> 直接查到相应的公网出口
>
> 也可以
>
> ~~~
> curl somesite  ##提供返回公网出口的服务
> curl getip.name
> ~~~



