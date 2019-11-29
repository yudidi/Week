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

bug:

1. mysql保存emoji表情,utf8mb4保存不了表情的问题
2. 用户昵称中的emoji编码在序列化之后,保存到数据库中会被截断

```
{"user_id":"15283","nickname":"
```

原因: mysql数据库的默认字符集utf8,只能存储3个字节的数据,标准的emoji表情是4个字节,所以要使用utf8mb4兼容四个字节

解决方案:
1. 将表字段字符集设置成utf8mb4 
2. 数据库连接也需要改为utf8mb4

```
alter database 库名 character set utf8mb4 collate utf8mb4_general_ci
```

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
