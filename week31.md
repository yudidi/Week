
# kibana搜索时 转义特殊字符

ELK：kibana使用的lucene查询语法

`+ - = && || > < ! ( ) { } [ ] ^ " ~ * ? : \ /`
以上字符当作值搜索的时候需要用`\`转义

`\(1\+1\)\=2`用来查询(1+1)=2

> https://segmentfault.com/a/1190000002972420


# 数据同步的2种情况

1. 由程序自动同步

强一致性。强制同步2个表。

2. 由用户触发后，才同步。 保证最终一致性。

懒加载

## Golang小数float64在实际工程中加减乘除的精度问题

> https://blog.csdn.net/muhongzhong/article/details/88880359

* golang 浮点类型数据精度损失问题的解决方案

> https://blog.csdn.net/mario08/article/details/80682093

# 英语语法

这里为什么不直接用 which 而用 in which 呢？

> http://ask.yygrammar.com/q-4831.html

# Join on时可以指定条件

```
LEFT JOIN insure_project ON insure_project.insure_id = insure.id AND insure_project.name = product_category.insure_amount_project 
WHERE ...
```
