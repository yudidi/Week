
# Q: mysql not null 和 default

* 目前记录的

> https://sourcegraph.com/search?q=repo:%5Egithub%5C.com/yudidi/Week%24+default&patternType=literal#1

该句的含义是，该字段不能为null，并且设置如果插入数据的时候不设置该字段的值的时候使用的默认值。
insert操作且不给该字段插值的时候，数据库判断该字段不能为null，于是便会找他的default值来写入数据库，
如果没有default值，要么报错，插入失败，要么插入成功给个警告(社区版为报错,商用版报警告,并插入空串'',详见下面运行情况)

由此可见如果`为了避免插入null值单纯设置not null是不够的`，在多数情况下可能`还需要用default`设置插入的时候没有设置值的情况下，数据库应该填入的默认值，否则可能引起插入失败。

> https://blog.csdn.net/u011866460/article/details/40783527

# Q: 什么情况要设置not null
