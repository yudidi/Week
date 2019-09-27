
# Tips

## golang方法中receiver为指针与不为指针的区别详析

https://www.nuoweb.com/scripts/3052.html


## Golang 函数耗时统计

* 借助defer

https://blog.csdn.net/K346K346/article/details/92673425

## mysql 如何预测sql的执行时间

## mysql数据库中，如果字符串中包含单引号或双引号，该怎么处理？


```
// content中的city字段
INSERT INTO insure_message_push(`type`,`user_code`,`content`) VALUES ('upload_sensors_wx_info','weixin_33936','{"user_id":"33936","nickname":"～fish～","sex":"男","city":"St. John's","":"Newfoundland and Labrador","create_time":"","counselor":""}');

```

1. 有3种方法，但是用\转义会导致json不能反序列化。 所以这里是把单引号直接替换为空字符串。

> https://blog.csdn.net/czh500/article/details/90721286


## pandas



# Share

## 费米估算

