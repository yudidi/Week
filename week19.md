


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


* 调度 分布式任务

日志记录: 2条日志，一个起始，一个结束。
1. 每个task需要完成哪些事情写入日志。
2. 整个task的完成情况。


* 语法：MySQL中INSERT INTO SELECT的使用

```
INSERT INTO a (field1,field2) SELECT * FROM(SELECT b.f1,c.f2 FROM b JOIN c) AS tb
```
https://www.cnblogs.com/RoadGY/archive/2011/07/22/2114088.html


* structToMapByJsonTag And removeEmptyFieldForMap

```
func structToMapByJsonTag(obj interface{}) (m map[string]interface{}) {
	t := reflect.TypeOf(obj)
	v := reflect.ValueOf(obj)
	var data = make(map[string]interface{})
	for i := 0; i < t.NumField(); i++ {
		f := t.Field(i)
		chKey := f.Tag.Get("json")
		data[chKey] = v.Field(i).Interface()
	}
	return data
}

func removeEmptyField(m map[string]interface{}) map[string]interface{} {
	for k, v := range m {
		switch v.(type) {
		case time.Time:
			if v.(time.Time).IsZero() {
				delete(m, k)
			}
		case string:
			if v == "" {
				delete(m, k)
			}
		}
	}
	return m
}
```

* go 语言中默认的类型识别

如果不声明类型的话，默认的类型都是占用64位（如果机器是32位的话，默认是32位）
`整形默认是int64`， 浮点型默认是float64


```
wantM: map[string]interface{}{
	"int":  int64(1),
	"int":  1, // 1默认识别为int64(1)
},
```

> https://www.jianshu.com/p/74dfcff555b3

* Golang神奇的2006-01-02 15:04:05

词法分析的一个步骤（分词）

> https://www.jianshu.com/p/c7f7fbb16932


* 在开发过程中使用git rebase还是git merge，优缺点分别是什么？

主要区别是：是否会又一个额外的分支合并的merge，并且分支树也会多一个分支。

> https://www.zhihu.com/question/36509119

## 业务打点数据上传方案

1. 业务侵入型。
问题，如果当时失败了如何处理。是否就放弃。

2. 读取数据库，定时任务上传
问题：需要增加一个update_at字段，标记更新时间，用于判断是否有变化，再次上传。
问题：需要判断定时任务的周期。判断是否需要去重，如何去重。



## mysql如何避免写出低性能的语句。
比如… 多表连接

## mysql更新记录时设置自动更新时间戳

```
`creat_time` timestamp NULL DEFAULT CURRENT_TIMESTAMP
`update_time` timestamp NULL DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP
```

> https://blog.csdn.net/qq_35835624/article/details/79485609

