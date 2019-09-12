
# Tips

## Q：上线导致的服务不可用或异常情况，如何处理

服务异常原因，原来的数据表增加了一组数据，同时增加了数据标签，需要使用标签进行筛选。

但是线上的服务代码是没有用标签进行筛选，所以导致线上接口返回的数据混入了 新增的一组数据，进而导致了异常。


## sql cross join

2表，笛卡尔积

## mysql 字段设置default为Null好，还是“”好，

数据库表某字段设置default为Null好，还是“”好，或者是Empty String好呢？
> https://segmentfault.com/q/1010000006758650/a-1020000006759600

## MySQL 的 null 和 not null

问题 1：我字段类型是 not null，为什么我可以插入 空值？

https://learnku.com/laravel/t/4741/you-may-need-to-know-about-mysqls-null-and-not-null