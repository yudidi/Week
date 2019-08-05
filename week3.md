Algorithm、Review、Tip、Share 简称ARTS

1.每周至少做一个 leetcode 的算法题 2.阅读并点评至少一篇英文技术文章 3.学习至少一个技术技巧 4.分享一篇有观点和思考的技术文章

TODO
改善包含数据库操作的测试流程，引入必要的测试。
因为测试对业务最熟悉，可以考虑需求阶段或编码阶段，向测试多请教，给出最基本的测试情况。
使用GO module，GOProxy

# Algorithm

https://leetcode.com/problems/two-sum/

** 方法1: 暴力求解 **

* 怎么想到的
2层循环罗列所有情况(i,j)匹配的情况，逐个检查2数和是否为target即可

```
func twoSum(nums []int, target int) []int {
    l := len(nums)-1 // index of last item
    for i:=0; i <= l;i++{
        for j:=i+1; j <= l;j++{
            if nums[i] + nums[j] == target {
                return []int{i,j}
            }
        } 
    }
    return []int{}
}
```
TODO 下周优化

# Review
* Unit Testing for REST APIs in Go

讲解了golang中如何比较方便的测试http接口。

PS. 我们公司的测试数据库是一个docker启动的mysql，所有的http接口测试都作用到这个mysql容器中，不会对实际的数据库产生影响。

> https://codeburst.io/unit-testing-for-rest-apis-in-go-86c70dada52d


# Tips

golang删除slice中特定条件的元素，优化版
https://blog.csdn.net/liyunlong41/article/details/85132603

// 20190805, 相同场景优化: 有2个slice,s1和s2,把s1中所有包含在s2中的元素去掉。
```
for i := 0; i < len(tmp.List); i++ {
    for _, hide := range hideInsureCodes {
        if tmp.List[i].InsureCode == hide {
            tmp.List = append(tmp.List[:i], tmp.List[i+1:]...)
            i--
        }
    }
}
```

# Share

https://codeburst.io/unit-testing-for-rest-apis-in-go-86c70dada52d
