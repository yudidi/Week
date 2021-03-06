Algorithm、Review、Tip、Share 简称ARTS

1.每周至少做一个 leetcode 的算法题 2.阅读并点评至少一篇英文技术文章 3.学习至少一个技术技巧 4.分享一篇有观点和思考的技术文章

# Algorithm
https://leetcode.com/problems/move-zeroes/
* 在上周代码基础上进行优化

上一次主要是运用的冒泡排序的思路，每趟都把一个0冒泡到末尾，然后下一个趟再对剩余数组进行冒泡。主要是交换0和非0元素。
本周采用一个全新的思路。思路的发现，参考一个博客。

* 新思路是如何想到的

因为题目要求把全部的0都放到后面，也就是说我从前往后，如果找到一个0，就跟后面!0元素进行交换，这样就可以把所有的0都交换到后面。
我们在脑海中运行一次[0,1,0,3,12]-> [1,0,0,3,12],然后再运算一次，可以发现我们需要知道2个位置信息才能完成交换，比如下一次交换的位置1和位置3。
位置1=0:表示非0元素数组的下一个元素（也就是下一个需要被交换的0的位置），位置3:位置1之后的第一个非0元素的位置。
我们需要2个指针k,cur来表示这2个位置。[0,k)是非0元素数组,k指向下一个需要被交换的0元素，cur从前往后扫描遇到非0元素即停止。

* 代码

这个代码寻着思路很容易写出来，但是一来就看代码，似乎不好理解。
关键点有2个：
1. [0,k)是循环不变量，其中都是非0元素，其含义从循环开始前至循环结束后，都不会改变
2. k含义的理解：表示非0元素数组后的第一个0. 这个0之后会与后面的非0元素进行交换。

```
func moveZeroes(nums []int)  {
    // [0,k) has !0 items.
    k := 0 // 循环不变量:[0,0),初始化：表示有0个!0元素。k表示
    for cur,_ := range nums{
        if nums[cur] != 0 { // 如果扫描到非0元素，那么就和k位置的元素
            nums[k],nums[cur] = nums[cur],nums[k]
            k++
        }
    }
}
```
> https://blog.csdn.net/camellhf/article/details/52607984

# Review
周末4.27，4.28号参加了Gopher China 2019大会。

* 听了David的全英文演讲: “How to writ testable code”

虽然讲的是大会中出现的最简单的知识点，但是他讲解的思路确实很清晰，训训善诱，娓娓道来。

TODO
https://link.zhihu.com/?target=http%3A//matt.might.net/articles/what-cs-majors-should-know/
ARTS打卡-第二周 - ruud的文章 - 知乎
https://zhuanlan.zhihu.com/p/60563499

# Tip
* 外连接的性能
有些用内连接就可以了，我以前都是直接用左连接，浪费了一些性能。
inner join | left join

* 如果原来的数据库表设计得不太好，又没有时间精力去重构的话，可以考虑使用view对一些常用的sql进行封装，简化客户端的代码

mysql视图的作用（详细）: https://www.cnblogs.com/sustudy/p/4166714.html
mysql视图优缺点： https://www.jianshu.com/p/48a02e3c98f3

* 使用golang的sort接口进行排序

本周遇到一个需求，有a,b,c3个元素，每个元素有2个属性：
属性1: 风险等级[取值：低，中，高]
属性2: 优先级[a,b,c]。
输出要求：
1. 只输出中高风险等级的元素
2. 等级高＞等级中
3. 相同风险等级按照a,b,c的顺序输出
我最开始使用if/else对所有情况进行的判断，代码很长，非常愚蠢，后来和同事讨论交流了一下，发现是可以用sort接口来进行简化处理的。

> https://www.jb51.net/article/89105.htm

# Share
Gopher China 2019大会，有2个内容我觉得对我近期有一定帮助。

## 1. 用golang替代python对知乎大部分项目进行重构的经验分享。
主要分为：
1. 为什么重构
2. 如何重构
3. 重构的一些经验

## 2. 代码测试

在公司的业务项目中，我发现我常常会很容易对不操作数据库的函数进行测试，但是函数一旦包含数据库操作，我就很难去写测试了，此时需求常常变动，代码改动很多，很容易在修复bug时引入新bug。

所以我是很愿意去写测试的，之前我一直想寻找一种仅仅在测试阶段运行在内存中的mysql数据库，测试完毕就销毁，但是似乎没有。

今天，我似乎找到了一种思路： 那就是用一个docker启动mysql，作为一种内存中的数据库，只有我们不挂载磁盘目录，那么这些数据就不会存储下来，每次测试完成后，停止mysql容器即可清除数据。 同时呢，我们在*_test.go代码中直接对http接口进行测试即可。这样整个过程就是不依赖具体对测试数据库，可以在任意环境进行自动化测试。


