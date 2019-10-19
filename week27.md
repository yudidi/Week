
# Tip

X-Forwarded-For

remote_addr和x_forwarded_for的区别

nginx转发的设置

> https://www.cnblogs.com/kuracola/p/7482939.html

> https://studygolang.com/articles/12971?fr=sidebar

* post,get,cookies模拟登陆

## An introduction to machine learning with scikit-learn

> https://scikit-learn.org/stable/tutorial/basic/tutorial.html

## 03-Jupyter-Notebook-Numpy-and-Matplotlib

* 3种数组

1. python数组 元素是任意类型的
2. python array: 指定元素类型的数组
3. numpy.array: 也有元素类型，具有向量和矩阵特点,便于处理

* 循环

1. python的arange
> 【python入门】arange()与range()的区别 https://blog.csdn.net/lyl771857509/article/details/78999925

2. np.arrange: step可以是float64

3. np.linspace:

* 矩阵乘法的意义和2种理解

1. 每天的销售总额: 单价矩阵(一维) * 销量矩阵(二维,每列代表1天的销量)

如果把单价矩阵增加几行，就可以计算出不同单价的销售总额

> https://blog.csdn.net/vernice/article/details/48510709

2. 
我们管这种从材料列表转为开销表的过程，就叫做一个线性映射

> https://www.cnblogs.com/mhpp/p/7661068.html

* 矩阵行列式

> https://blog.csdn.net/DrIcetar/article/details/81297446

* 线性代数：如何求矩阵的逆矩阵

> https://jingyan.baidu.com/article/da1091fb69f0b7027849d612.html

* np.percentile: 百分位数

分位数是用于衡量数据的位置的量度

1. 用99个数值或99个点，将按大小顺序排列的观测值划分为100个等分，则这99个数值或99个点就称为百分位数，分别以Pl，P2，…，P99代表第1个，第2个，…，第99个百分位数。

2. 中位数是第50百分位数。

> https://baike.baidu.com/item/%E7%99%BE%E5%88%86%E4%BD%8D%E6%95%B0/10064171?fromtitle=percentile&fromid=12015307&fr=aladdin

## 矩阵基础MOOC

https://www.icourse163.org/learn/TONGJI-481001?tid=1206883240#/learn/content?type=detail&id=1211787764&cid=1214717041

## 数据库设计

```
A: 表示app用户id(记为aid), 公司有多个app
B: 微信unionid(记为uid). 一个公司就一个uid. 
C: 表示小程序用户id(记为xid). 公司有多个小程序
A->B: 多对1，表示多个app用户对应1个微信uid.比如 (aid1,uid),(aid2,uid)
C->B: 多对1, 表示多个小程序用户对应1个微信id. 比如(xid1,uid),(xid2,uid)
A->C: 1对1，表示1个app用户 和 小程序用户 是一一对应的。比如(aid1,xid1) (aid2,xid2)
```
