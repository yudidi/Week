
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

## 决策树模型的解释性就很强

当我们发现，我们的数据中分类变量比较多，我们尝试采取决策树进行建模，

具体理由：我们做出来的模型需要指导业务人员进行使用，那么要求做出来的模型的可解释要高，而决策树模型的解释性就很强，那么业务人员理解起来就会很容易，那么之后进行应用就不用再专门进行对业务人员的培训，直接让他按照模型做出来的结果进行后续的业务，会提升效率。

> https://www.lizenghai.com/archives/30440.html

* 决策树缺点

> https://www.jianshu.com/p/69dbb042a0e3

## pandas

### Pandas分组与聚合
1.分组 (groupby)
一、GroupBy对象：DataFrameGroupBy，SeriesGroupBy
二、GroupBy对象支持迭代操作
三、GroupBy对象可以转换成

> https://cloud.tencent.com/developer/article/1193823

### 字符串,列修改

* 截取'股票代码'第一个字符
df['首字符'] = df['股票代码'].str[0:1]

* 根据一列的值，修改另一列的值 
> https://www.cnblogs.com/sxinfo/p/10663014.html

### series

sort_values
sort_index

### series可视化

* line,bar : The Difference Between Bar Graphs and Line Graphs

Line可以同时对比多个部门的变化趋势

Bar查看单一部分的变化时，数据更清晰

* 箱形图

来可视化每列中值的分布。> https://www.yiibai.com/pandas/python_pandas_visualization.html

# Share

## 费米估算

