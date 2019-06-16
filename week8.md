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

* 借鉴的思路3：

对题目的理解不到位：

1. 输入是排序数组。
2. 输出是：按照顺序去重后的数组(原地去重) + 去重数组长度。

怎么想到的: 举例子，观察输入和输出: 1,1,2,2,3 -> 1,2,3 (3). 可以发现 第1个出现的2，需要换到第二个1的位置。 也即是说：去重的数组的每个值都是第一次出现的那个重复的数组交换过来的。这样就容易产生一个遍历+交换/覆盖的思路。

运行未通过

```
// 1,1,2 -> 1,2
// [0,l]表示去重后数组  // i:表示下一个要处理的元素
func removeDuplicates(nums []int) int {
    l := 0 // [0,0]
    n := len(nums)
    for i:=1;i<n-1;i++{
        if nums[i] == nums[l]{
            continue
        }else{ // i != l, find another element nums[i]
            l++
            nums[l],nums[i] = nums[i],nums[l]
        }
    }
    nums = nums[0:l]
    return len(nums)
}
```

难点：2个指针的含义不明，初始状态没有很好的定义出来

https://blog.csdn.net/u014627807/article/details/79383955

* 借鉴思路3plus：

快慢指针：慢指针[0,l]表示去重后的数组，快指针r用于寻找首次出现的不同数组，然后把swap(l+1,r)，用于扩展去重数组。

错误：交换导致去重数组中的值被交换到数组后面，从而导致了问题。

```
// 1,1,2 -> 1,2
// [0,l]表示去重后数组  // i:表示下一个要处理的元素
func removeDuplicates(nums []int) int {
    l := 0 // [0,0]
    n := len(nums)
    for r:=1;r<n-1;r++{
        if nums[r] == nums[l]{
            continue
        }else{ // find a number
            l++
            nums[l] = num[r] // YC: 是覆盖，不是交换。交换会把num[l]交换到后面的nums[r]，从而导致问题。
        }
    }
    nums = nums[0:l+1]
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
