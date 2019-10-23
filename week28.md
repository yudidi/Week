
## KNN

* 距离算法

欧拉距离  euclidean_distance (l2)

曼哈顿距离(出租车距离) manhattan_distance (l1)

明可夫斯基距离 minkowski_distance (l_p) 

###  KNeighborsClassifier参数

```
1. weights 
'uniform'：不管远近权重都一样，就是最普通的 KNN 算法的形式。
'distance'：权重和距离成反比，距离预测目标越近具有越高的权重。
自定义函数：自定义一个函数，根据输入的坐标值返回对应的权重，达到自定义权重的目的。

2. metric：指定距离度量方法，一般都是使用欧式距离。
  'euclidean' ：欧式距离. p无效
  'manhattan'：曼哈顿距离。p无效
  'chebyshev'：切比雪夫距离。p无效
  'minkowski'： 闵可夫斯基距离，默认参数. p=1 => manhatta. p=2 =>  euclidea 
3. p：和metric结合使用的，当metric参数是"minkowski"的时候，p=1为曼哈顿距离， p=2为欧式距离。默认为p=2。
```

> https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.KNeighborsClassifier.html#sklearn.neighbors.KNeighborsClassifier
