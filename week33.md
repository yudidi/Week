# mysql LIKE的字符串拼接

```
SELECT xxxx FROM t
WHERE
 is_displayed = TRUE AND case_code LIKE ? [%7%]
 ```
# mysql字段为NULL和golang结构体字段为json.RawMessage

1. NULL字段反射到json.RawMessage会导致panic，只能反射到string [R2]
2. 数据库预编译语句的?遇到nil指针时,会被转换为NULL。

```
if userCode == "" {
			userId = nil
		} else {
			userId = userCode
		}
		if _, err = this.dao.conn.Insert(
			"INSERT xxxx (user_id) VALUES(?)", // 相当于 VALUES(NULL)
			userId,
		)
```

# mysql保存不了emoji表情

## MySQL修改表、字段、库的字符集及字符集说明

> https://www.cnblogs.com/qiumingcheng/p/10336170.html

bug:

1. mysql保存emoji表情,utf8mb4保存不了表情的问题
2. 用户昵称中的emoji编码在序列化之后,保存到数据库中会被截断

```
{"user_id":"15283","nickname":"
```

原因: mysql数据库的默认字符集utf8,只能存储3个字节的数据,标准的emoji表情是4个字节,所以要使用utf8mb4兼容四个字节

解决方案1:
1. 将表字段字符集设置成utf8mb4 
2. 数据库连接也需要改为utf8mb4

```
DATABASE_DSN=root:password@tcp(IP:port)/db?charset=utf8mb4
```

解决方案2:
把数据库表设置为字符集设置成utf8mb4 

> https://www.cnblogs.com/houss/p/11131935.html

# golang channel 任务队列

TODO

```
nextSig := make(chan bool, 1)
nextSig <- true
for {
	select {
	case <-nextSig:
		if this.doMessagePush() > 0 {
			nextSig <- true
		} else {
			time.Sleep(10 * time.Second)
			nextSig <- true
		}
	}
}
```

# golang 增加5秒时间 时间操作

time.Now().Add(time.Duration(i*5)*time.Second)


# golang 网络问题

* 这个异常"net/http: request canceled while waiting for connection (Client.Timeout exceeded while awaiting headers" 是什么场景下产生的呢

# MySQL的字符集与字符排序规则
https://blog.csdn.net/Strong997/article/details/99618372
https://www.cnblogs.com/kerrycode/p/11170266.html

# 彻底理解cookie，session，token

1. 无状态 
Q: 如何做到无状态,stateless. 做到不存储session,实现身份验证。
A: `发令牌(token)`
1. 在服务端生成token:对用户标记(如,user_id)签名
2. 通过http header发放给用户
3. 用户请求的header中带着这个token访问服务器
4. 服务验证token,验证通过则视为登录过,否则认为用户没有认证,需要重新登录

这样一来,我就不保存session id了,我只是生成token,然后验证token,我用我的`CPU计算时间获取了我的session 存储空间`

> https://www.cnblogs.com/moyand/p/9047978.html
