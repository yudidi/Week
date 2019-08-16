# Algrithm

https://leetcode.com/problems/maximum-subarray/

* 优化解法：分治法求解

https://blog.csdn.net/lw_power/article/details/80892362


# Tip

使用plantuml生成GO的类图

> https://www.jianshu.com/p/e829f78efc20 如何阅读复杂项目的源码

* MySQL 字符串截取函数：left(), right(), substring(), substring_index()。

还有 mid(), substr()。其中，mid(), substr() 等价于 substring() 函数，substring() 的功能非常强大和灵活。

```
4.2 截取第二个 '.' （倒数）之后的所有字符。
mysql> select substring_index('www.example.com', '.', -2);
+-------------------------------------------------+
| substring_index('www.example.com', '.', -2) |
+-------------------------------------------------+
| example.com                                          |
+-------------------------------------------------+
```
> https://www.cnblogs.com/zdz8207/p/3765073.html

## 任务调度框架，执行思路

借鉴openaccount的task调度框架，基于一个日志表log，进行生产和消费消息。

* 生产者
往log表插入task

* 消费者
从log表读取task，根据task类型做不同处理。

编写一个统一的消费函数，封装以下共同逻辑：
1. task执行前统一修改状态。task的状态更新: 0:待处理,1:处理中,2:处理成功,3:处理失败。
2. task执行后的统一更新状态。
3. task错误信息的记录。

* 要求：该log表能够兼容所有类型的task的存储。
```
  `id` int(10) unsigned NOT NULL AUTO_INCREMENT,
  `type` varchar(32) NOT NULL COMMENT 'private:私信,template:模板消息',
  `user_code` varchar(32) NOT NULL,
  `mobile` varchar(32) NOT NULL DEFAULT '',
  `content` text COMMENT '内容',
  `status` tinyint(4) NOT NULL DEFAULT '0' COMMENT '0:待处理,1:处理中,2:处理成功,3:处理失败',
  `additional` text COMMENT '错误信息',
  `create_at` datetime NOT NULL DEFAULT CURRENT_TIMESTAMP,
  `notify_at` datetime NOT NULL DEFAULT CURRENT_TIMESTAMP,
```

* Q: 如何防止重复发送消息。 生产不重复，消费不重复。

## 系统设计

go语言实现分布式crontab任务系统
> https://blog.csdn.net/oXiaoBuDing/article/details/89085351

## 分布式任务调度
* 任务调度系统 1.0
* 任务调度系统 2.0
a. 群首选举
b. 脑裂问题
c.发现存活的客户端

https://juejin.im/post/5c55ac0bf265da2da771a216

## select 需要加rollback吗 mysql


https://stackoverflow.com/questions/28614571/why-do-i-need-to-rollback-a-select-in-mysql-innodb
