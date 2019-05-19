
Algorithm、Review、Tip、Share 简称ARTS

1.每周至少做一个 leetcode 的算法题 2.阅读并点评至少一篇英文技术文章 3.学习至少一个技术技巧 4.分享一篇有观点和思考的技术文章

# Algorithm
https://leetcode.com/problems/two-sum/

* 这里是使用先构造全部查找表，然后再判断查找表中是否存在(target-cur)
```
func twoSum(nums []int, target int) []int {
	numsMap := make(map[int]int)

	for i, n := range nums {
		numsMap[n] = i
	}

	for i, n := range nums {
		j, ok := numsMap[target-n]
		if ok && j != i {
            return []int{i, j}
		}
	}
	return []int{}
}
```

* 考虑是一个排序的数组

https://leetcode.com/problems/two-sum-ii-input-array-is-sorted/

思路：排序数组总是往二分查找上靠。

思路1. 仍然是两次遍历，外层遍历数组nums,当前被处理元素用cur表示，通过二分法查找target-cur. 时间复杂度:n*logn.

思路2. 基于排序的特点. 在[l,r]中寻找和为sum的2个数.

首尾2个元素l+r与target相比, 
1. l+r = target, find it.
2. l+r < target,那么应该再找一个更大的元素，只能是从l往后找，所以 和为targe的2个元素应该在[l+1,r].
3. l+r > target,那么应该再找一个更小的元素，只能是从r往前找，所以 和为targe的2个元素应该在[l,r-1].

从实现上来说，因为不知道循环多少次，用while循环，也就是`for;;`

```
func twoSum(numbers []int, target int) []int {
    n := len(numbers)
    i,j:=0,n-1
    for;;{
        r := numbers[i] + numbers[j]
        if r == target {
            return []int{i+1,j+1}
        }else if r > target{
            j--
        }else{
            i++
        }
    }
}
```

# Review
目前在用流利说学习英语口语，英文文章阅读暂缓。

# Tip

golang传递数组的指针
items *[]*DetailItemVO

https://stackoverflow.com/questions/36242018/golang-pointer-to-slice-and-array

包学习
https://golang.org/pkg/container/heap/

* 测试数据的准备
通过sql还是http接口呢？


Q：float64精度问题。
A： 给出来的是最终解决方案。钱这种东西，从来都不是浮点类型。
A： https://blog.csdn.net/wslyk606/article/details/81333001
go语言中float64 保留2位小数

微服务化，家庭成员获取接口，visible统一处理。

Q: mysql关于 inner join 数据重复问题
https://blog.csdn.net/qq_29498555/article/details/79695815

# Share

领域驱动架构（DDD）建模中的模型到底是什么？ - 何明璐的回答 - 知乎
https://www.zhihu.com/question/25089273/answer/69859648

这篇文章开头就和我2年左右的开发经验达成了共识，所以我继续看下去了.
```
拿到这个功能需求后当然是首先要详细阅读具体的业务功能需求，在阅读完后第一需要思考的不是业务流程，不是数据库表，而是首先应该思考该功能对应的核心领 域对象究竟是什么？
```
就我2年左右的开发经验而言，我们在需求评审环节，主要的目的都是去明确业务流程或者数据库表结构,明确之后就进行开发了。



