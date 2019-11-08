

# mysql

* "Prepared statement contains too many placeholders"

## 事务的作用语句

```
COMMIT / ROLLBACK这两个命令用的时候要小心。
COMMIT / ROLLBACK 都是用在执行DML语句（INSERT / DELETE / UPDATE / SELECT ）之后的。
DML语句执行完之后，处理的数据，都会放在回滚段中（除了 SELECT 语句），等待用户进行提交（COMMIT）或者回滚（ROLLBACK），当用户执行 COMMIT / ROLLBACK后，放在回滚段中的数据就会被删除。
```
> https://blog.csdn.net/chenlycly/article/details/21302073

## mysql 锁表的情况

> https://blog.csdn.net/qq_27409289/article/details/85726453

> https://www.cnblogs.com/paul8339/p/6877729.html

## mysql事务太长未提交，是否导致问题

## 开发和上线流程中的, 分支管理

## 数据库设计（一对一，一对多，多对多）关联查询

> https://blog.csdn.net/jrdgogo/article/details/52212418


## nginx做反向代理

> https://www.jianshu.com/p/0b6f80949503

* 正向代理代理客户端，反向代理代理服务器。

客户端 -> 正向代理 =>...=> 反向代理 -> 服务器

* 浏览器输入地址后

浏览器:wwww.123.com -> nginx(从虚拟主机代理到真实服务器)(www.123.com:80->http://127.0.0.1:8080) -> 真实服务器(127.0.0.1:8080) -> 内容返回给浏览器/用户。

对于用户来说,看到的wwww.123.com的内容实际上是真实服务器的内容

```
server {
        listen       80; // ND: 关键配置. 用于配置监听nginx的哪些端口,监听哪些IP地址的连接
        server_name  www.123.com; // YW: 这个只是'基于名称的虚拟主机' // 也可以用'基于 IP 地址的虚拟主机配置'

        location / {
            proxy_pass http://127.0.0.1:8080; // YW: 该指令用于设置被代理服务器的地址。可以是主机名称、IP地址加端口号的形式。
            index  index.html index.htm index.jsp;
        }
    }  
```

* `listen的配置`

1. listen *:80 | *:8080    #监听所有80端口和8080端口 // TODO
2. listen  IP_address:port #监听指定的地址和端口号
3. listen  IP_address      #监听指定ip地址所有端口   // 
4. listen port             #监听该端口的所有IP连接   // YC: 表示该nginx的该port端口的所有IP连接都被监听。

> https://www.cnblogs.com/ysocean/p/9392908.html#_label2


