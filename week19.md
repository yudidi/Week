


# Tip

 ```
CREATE TABLE `insure_family_member` (
  `id` int(10) unsigned NOT NULL AUTO_INCREMENT,
  `user_id` int(10) unsigned NOT NULL DEFAULT '0' COMMENT '用户id',
  `name` varchar(128) NOT NULL DEFAULT '' COMMENT '姓名',
  `user_relation` varchar(128) NOT NULL DEFAULT '' COMMENT '家庭成员是用户的XXX',
  `job` varchar(256) NOT NULL DEFAULT '' COMMENT '工作',
  `tag` varchar(128) NOT NULL DEFAULT '' COMMENT '标签',
  PRIMARY KEY (`id`),
  UNIQUE KEY `user_id` (`user_id`,`name`,`user_relation`)
) ENGINE=InnoDB AUTO_INCREMENT=6844 DEFAULT CHARSET=utf8

ALTER TABLE `insure_family_member` MODIFY COLUMN `user_relation` VARCHAR(128) DEFAULT NULL COMMENT '家庭成员是用户的XXX';

```

* 毕竟在 MySQL 中认为 NULL 代表着“未知”。 
在 SQL 中，任何值与 NULL 的比较返回值都是 NULL 而不是 TRUE, 就算 NULL 与 NULL 的比较也是返回 NULL。

MySQL 唯一性约束与 NULL
> https://yemengying.com/2017/05/18/mysql-unique-key-null/
