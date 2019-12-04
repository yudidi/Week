# Algorithm

# Tips

## processon

1. anaconda
安装，数据基本清洗，数据可视化 (TODO 图可以配置label和偏移等)

2. 统计学概念

* mean,median,mode

* 方差、标准差

Q: 既然有了方差来描述变量与均值的偏离程度，那又搞出来个标准差干什么呢

* 偏态与峰度

* 四分位

根据4分位，计算值的上界和下界。可用于判断异常值(Q3-Q1)*k,k=[1.5,3]

3. 数据质量的准则
> https://www.processon.com/mindmap/5d7f0d6ae4b0ca809fccda33

4. 费米估算

Q：芝加哥有多少钢琴调音师

```
# 假设
芝加哥约有500万人居住
平均每个家庭有2人
大约1/20家庭有定期调音的钢琴
平均每台钢琴每年调音一次
每个调音师调整一台钢琴需要2小时
每个调音师每天工作8小时，每周5天，每年50周。
# 计算
```

## insert into ... on duplicate key 多条数据问题

```
INSERT INTO  test4(id,cnt) VALUES
 (167,2),
 (4,3),
 (6,5),
 (7,9)
  ON DUPLICATE KEY UPDATE id = VALUES(id), cnt= VALUES(cnt)+  cnt 
```

## mysql中int(3)与int(11)有什么区别吗？[R2]

* 要查看出不同效果记得在`创建类型的时候加zerofill`这个值，表示用0填充，否则看不出效果的。

> https://www.cnblogs.com/yaowen/p/8862108.html

对于存储和计算没有区别，只是显示效果上的区别。

> https://segmentfault.com/q/1010000000257234


## pandas 数据处理教程

```
1. Series 和 DataFrame
2. mean,median,mode

3. 选择列
df = df[['a','b','c']] # 注意是嵌套的[]

4. 选择行
df = df[df['a']>0][df['b'>0]] # 往后增加筛选条件即可

5. 处理异常值
df.dropna() # 去掉NAN的行

```

> https://www.yiibai.com/pandas/python_pandas_series.html

### FAQ

dataframe的字符类型dtypes为什么是object,而不是str？
> https://segmentfault.com/q/1010000012226229

pandas 数据类型转换
> https://www.cnblogs.com/onemorepoint/p/9404753.html

## Anaconda完全入门指南
1. 安装 
2. 用anaconda来创建我们一个个独立的python环境

> https://www.jianshu.com/p/eaee1fadc1e9

# Review

## 数据分析到底该怎么学？

> https://www.infoq.cn/article/oxoekbQ-loWOl38doEmT

## Python数据分析-基础技术篇

> https://www.imooc.com/learn/843

