
# Algorithm、Review、Tip、Share 简称ARTS

1.每周至少做一个 leetcode 的算法题 2.阅读并点评至少一篇英文技术文章 3.学习至少一个技术技巧 4.分享一篇有观点和思考的技术文章

# Algorithm
https://leetcode.com/problems/search-insert-position/

* 思路
数组是有序的. 
发现这个函数需要做2件事情:
1. loop and find index if target. 这个用二分查找就可以作答
2. find insert position

* 提交未通过
```
func searchInsert(nums []int, target int) int {
    // loop and find it index
    l := 0
    r := len(nums)-1
    var insert int
    for ;; {
        m = l + (r-l)/2
        if target == nums[m] {
            return m
        }else if target > nums[m] {
            l = m+1 // [m+1,r]
            insert = m+1
        }else {
            r = m-1 // [l,m-1]
            insert = m1
        }
    }
    return insert
    // find insert position
}
```

```
输入：
[1,3,5,6]
0
输出：
-1
预期：
0
```

* 修正边界情况后，解答通过。
插入右边界和左边界，处理方法是不同的，通过给出的测试用例进行分析即可知道。

```
func searchInsert(nums []int, target int) int {
    // loop and find it index
    l := 0
    r := len(nums)-1
    var insert int
    for ;l<=r; {
        m := l + (r-l)/2
        if target == nums[m] {
            return m
        }else if target > nums[m] {
            l = m+1 // [m+1,r]
            insert = m+1  // 插入右边界，可以+1。
        }else {
            r = m-1 // [l,m-1]
            insert = m  // 插入左边界，是不能-1。 PS. 左边界需要特殊处理
        }
    }
    if insert == -1 { // PS. 左边界需要特殊处理
        return 0
    }
    return insert
    // find insert position // 要注意target在边界的情况，插入左边界和右边界
}
```

# Tip 

* MySql只支持Union(并集)集合运算，好像也是4.0以后才有的；一般的解决方案用in和not in来解决，小量数据还可以，但数据量大了效率就很低了
https://blog.csdn.net/mine_song/article/details/70184072

## 数据库库设计

除非不得已，不要设计拼接的字符串，而是利用关系型数据库的本身的性质。用于关系表存储，而不是拼接的方式进行存储。

四种设计方案：

1. 关系表：产品id+搜索条件
2. 关系表：搜索条件+产品ID

* bug修改问题. Code Review.

去重问题
1. 有序数组去重
删除元素的算法不同，效率不同。

2. 无序数组去重
3. 删除数组中元素，下标的联动变化问题

一个典型的无序数组去重问题。 > https://git.lcgc.work/insurance/service/merge_requests/353/diffs

```
for _, r := range response.List {
		for j := 0; j < len(r.Products)-1; j++ {
			cur := r.Products[j]
			for k := j + 1; k < len(r.Products); k++ {
				if cur.ProductId == r.Products[k].ProductId {
					if cur.InsuranceType > r.Products[k].InsuranceType {
						response.List[j].Products = append(r.Products[:j], r.Products[j+1:]...)
					} else {
						response.List[j].Products = append(r.Products[:k], r.Products[k+1:]...)
					}
					break
				}
			}
		}

```

* 如何遍历结构体
https://www.golangtc.com/t/52c4e367320b525eb500004e


* golang 字符串的修改，微信收藏图片

* mysql杀死死锁的事务

https://www.cnblogs.com/topicjie/p/7323248.html

* 我的开发流程的问题

1. 需求评审
2. 设计评审

目前的问题
1. 需求应该达到的目标: 有一个基本的思路，然后可以较快的写出接口文档，明确这些接口实现的思路。
2. 不能省略开发流程中的步骤: "设计评审",评审文档和具体接口实现逻辑。


* Golang 大杀器之性能剖析 PProf
https://www.jianshu.com/p/4e4ff6be6af9

* 正则: ^和$符合, 判断相等

^(70岁)$|^(终身)$"

* kibana的使用


# Share

https://blog.csdn.net/basonson/article/details/50924466

数据中台演进的四个阶段
https://www.jiqizhixin.com/articles/2019-04-23-4
