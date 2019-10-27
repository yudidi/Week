# Algrithm

查找 sum>=s 的最短连续子数组.

* brute force -> better brute force -> bs(TODO) -> 4. two pointers / 滑动窗口

4.1 two pointers 

```
int minSubArrayLen(int s, vector<int>& nums)
{
    int n = nums.size();
    int ans = INT_MAX;
    int left = 0;
    int sum = 0;
    for (int i = 0; i < n; i++) {
        sum += nums[i];
        while (sum >= s) {
            ans = min(ans, i + 1 - left);
            sum -= nums[left++];
        }
    }
    return (ans != INT_MAX) ? ans : 0;
}
```

4.2 滑动窗口
```
int minSubArrayLen(int s, vector<int>& nums) {
      int l = 0 , r = -1; // nums[l...r]为我们的滑动窗口
      int sum = 0;
      int res = nums.size() + 1;
      while(l < nums.size()){   // 窗口的左边界在数组范围内,则循环继续
          if(r + 1 < nums.size() && sum < s)
              sum += nums[++r];
          else // r已经到头 或者 sum >= s
              sum -= nums[l++];
          if(sum >= s)
              res = min(res, r - l + 1);
      }
      if(res == nums.size() + 1)
          return 0;
      return res;
  }
```
> https://leetcode.com/problems/minimum-size-subarray-sum/solution/

# Share

* How to: Work at Google — Example Coding/Engineering Interview

以"two sum"为例,讲解算法面试应该注意的地方。

1. 预先思考

2. 边写边讲解

3. 测试你的代码

https://www.youtube.com/watch?v=XKu_SEDAykw

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

2. metric：  指定距离度量方法，一般都是使用欧式距离。 string or callable, default ‘minkowski’
  'euclidean' ：欧式距离. p无效
  'manhattan'：曼哈顿距离。p无效
  'chebyshev'：切比雪夫距离。p无效
  'minkowski'： 闵可夫斯基距离，默认参数. p=1 => manhatta. p=2 =>  euclidea 
  
3. p：和metric结合使用的. 只有metric=“minkowski”,p才起作用
当metric参数是"minkowski"的时候，p=1为曼哈顿距离， p=2为欧式距离。
默认为p=2。
```
> https://scikit-learn.org/stable/modules/generated/sklearn.neighbors.KNeighborsClassifier.html#sklearn.neighbors.KNeighborsClassifier
> http://www.py3study.com/Article/details/id/3284.html

## CI

* Stages

两个有价值的提示：

如果配置文件中没有定义stages，那么默认情况下的stages属性为build、test和deploy。

如果一个job没有定义stage属性，则它的stage属性默认为test。

* Jobs

> gitlab-ci.yml配置说明（官方文档翻译）
https://www.szyhf.org/2017/01/16/gitlab-ci-yml%E9%85%8D%E7%BD%AE%E8%AF%B4%E6%98%8E%EF%BC%88%E5%AE%98%E6%96%B9%E6%96%87%E6%A1%A3%E7%BF%BB%E8%AF%91%EF%BC%89/

> https://segmentfault.com/a/1190000019540360
