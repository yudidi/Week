# Algorithm

## 数据分析相关算法


# Tips

## insert into ... on duplicate key 多条数据问题

```
INSERT INTO  test4(id,cnt) VALUES
 (167,2),
 (4,3),
 (6,5),
 (7,9)
  ON DUPLICATE KEY UPDATE id = VALUES(id), cnt= VALUES(cnt)+  cnt 
```


## mysql中int(3)与int(11)有什么区别吗？

> https://www.cnblogs.com/yaowen/p/8862108.html

对于存储和计算没有区别，只是显示效果上的区别。

> https://segmentfault.com/q/1010000000257234


## pandas 数据处理教程

> https://www.yiibai.com/pandas/python_pandas_series.html

### FAQ

dataframe的字符类型dtypes为什么是object,而不是str？
> https://segmentfault.com/q/1010000012226229

## Anaconda完全入门指南

> https://www.jianshu.com/p/eaee1fadc1e9

# Review

## 数据分析到底该怎么学？

> https://www.infoq.cn/article/oxoekbQ-loWOl38doEmT

## Python数据分析-基础技术篇

> https://www.imooc.com/learn/843
