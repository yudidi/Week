## mysql中if()函数,ELT()函数

在mysql中if()函数的用法类似于java中的三目表达式，其用处也比较多，具体语法如下：
IF(expr1,expr2,expr3)，如果expr1的值为true，则返回expr2的值，如果expr1的值为false，

则返回expr3的值。

* MySQL的if，case语句使用总结

> https://www.cnblogs.com/raobenjun/p/7998467.html

* MYSQL中可以实现类似IF判断的方法

如下：sex：1-男，2-女，3-未知；level是客户的级别：1-超级VIP客户，2-VIP客户，3-普通客户

ELT()函数

> https://blog.csdn.net/rocling/article/details/82147981


## 区块链如何运用merkle tree验证交易真实性

> https://www.tangshuang.net/4117.html


## mysql 中int类型字段unsigned和signed的探索

* 探索一：正负数问题

* 探索二：性能问题

> https://www.cnblogs.com/wangzhongqiu/p/6424827.html


## Q: mysql NOT NULL 和 DEFAULT 0 有必要同时加上吗?


## mysql date 按照字符串比较时,日期格式不同，导致字符串比较错误。

```

SELECT DATE_FORMAT(NOW(),'%Y-%m-%d') >= '2019-12-05' FROM insure_coupon_activity LIMIT 1;
SELECT DATE_FORMAT(NOW(),'%Y-%m-%d') >= '2019-12-05 00:00:00' FROM insure_coupon_activity LIMIT 1;

SELECT DATE_FORMAT(NOW(),'%Y-%m-%d %H:%M:%S') >= '2019-12-05' FROM insure_coupon_activity LIMIT 1;
SELECT DATE_FORMAT(NOW(),'%Y-%m-%d %H:%M:%S') >= '2019-12-05 00:00:00' FROM insure_coupon_activity LIMIT 1;
```

# 后端编程+数据分析

