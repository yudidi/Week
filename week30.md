

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


# 开发和上线流程中的, 分支管理
