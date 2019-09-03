



# Tips

## 错误处理原则

首先，对于影响后端数据的，后端需要进行约束。
不影响后端数据，请求明显非用户触发的，需要和运维一起处理。
比如对爬虫进行封禁；
用户触发的，需要前端进行处理，必要时后端也可加约束。

## TODO mysql 最大连接数为1，导致某种死锁。

```
f1(){
this.conn.query() // 使用1个连接
//
f2()
}

f2(){
this.conn.query() // 无法新增连接数，导致某种死锁TODO
}
```

## mysql 不能使用嵌套事务

```
Transactions cannot be nested. This is a consequence of the implicit commit performed for any current transaction when you issue a START TRANSACTION statement or one of its synonyms.

Statements that cause an implicit commit cannot be used in an XA transaction while the transaction is in an ACTIVE state.
```


*  Will a mysql transaction work if multiple connections are used for the queries?

https://stackoverflow.com/questions/8377566/will-a-mysql-transaction-work-if-multiple-connections-are-used-for-the-queries

* Behavior of transactions on multiple connections

https://dba.stackexchange.com/questions/140975/behavior-of-transactions-on-multiple-connections
