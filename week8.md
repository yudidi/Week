Algorithm、Review、Tip、Share 简称ARTS

1.每周至少做一个 leetcode 的算法题 2.阅读并点评至少一篇英文技术文章 3.学习至少一个技术技巧 4.分享一篇有观点和思考的技术文章

# Algorithm
https://leetcode.com/problems/remove-duplicates-from-sorted-array/

思路1: 使用map记录不同数字出现的次数，然后遍历map出现次树>2的元素进行删除。
不满足空间复杂度O(1)的前提。

思路2: 从题目要求来看，应该是只能用一个中间变量。 注意是排序数组，所以关键是如何知道相同元素的第一个和最后一个元素的位置。

```
func removeDuplicates(nums []int) int {
    m := make(map[int]int) // 使用map存放所有数字 -> 使用map存放前一个出现的数字
    
    m[nums[0]] = 1
    for i,v := range nums{
        if _,e := m[v]; e {
            nums = append(nums[:i],nums[i+1:]...) // 一遍删除，一遍序号会变化吧?
        }else{
            m[v] := 1
        }
    }
    return len(nums)
}
```


# Review
目前在用流利说学习英语口语，英文文章阅读暂缓。

# Tip

## Q: 为什么很多框架中会有大量只有一条return语句的函数存在
源源不断的需求变更，迟早会把你当初还算满意的代码结构修改的面目全非，所以即便是一条简单的赋值语句，也最好把它封装在函数里吧。
因为你不知道什么时候来了一个需求会改变它。这样即便是反复的修改，也不会影响到主体代码结构的可读性。
也算是明白了，为什么很多框架中会有大量只有一条return语句的函数存在。

## MySQL唯一索引和普通索引运行原理和使用选择
https://blog.csdn.net/Srodong/article/details/88838046

## MySQL索引原理以及查询优化
https://www.cnblogs.com/bypp/p/7755307.html

## 干货 MySQL常见的面试题 + 索引原理分析
https://www.cnblogs.com/blogtech/p/10530794.html

# Share

## context 专题

context的作用：
考虑有一个goroutine专门用于监控。
考虑从一个goroutine1中创建的多层嵌套的goroutine，我们需要取消所有的goroutine,如何做到取消以goroutine1作为树根的所有创建的goroutine。

https://github.com/developer-learning/reading-go/issues/191

https://www.flysnow.org/2017/05/12/go-in-action-go-context.html


## context的取消特性，导致的一些坑
https://zhuanlan.zhihu.com/p/34417106
