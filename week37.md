# 二分查找及其变式 

# docker k8s


* idea go单元测试 报错

```
command-line-arguments
.\calc_test.go:8:12: undefined:
```
> https://segmentfault.com/q/1010000011556752


## docker 安装redis 以及配置连接

https://juejin.im/post/5ca59dece51d4508b32a1292

四个配置需要处理好,否则idea程序连不上

```
bind
protected-mode
requirepass
daemonize yes 
```

* redis.conf配置有误,使用默认配置反而idea可以成功连接

## redis clients

https://redis.io/clients#go

## Q: 访问docker容器的redis失败.

如何使用Mac命令行建立一个TCP连接？
https://blog.csdn.net/ToraNe/article/details/102730379

Telnet测试自己写的TCP服务器
https://blog.csdn.net/asia66/article/details/81114721

```
(base) didis-mbp:tmp didiyu$ docker exec -it redis /bin/bash
OCI runtime exec failed: exec failed: container_linux.go:344: starting container process caused "exec: \"/bin/bash\": stat /bin/bash: no such file or directory": unknown
(base) didis-mbp:tmp didiyu$ docker exec -it redis /bin/sh
```

> https://blog.csdn.net/a19891024/article/details/80666353



Go语言学习之9 网络协议TCP、Redis与聊天室
https://www.cnblogs.com/xuejiale/p/10473503.html
