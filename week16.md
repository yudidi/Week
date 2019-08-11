Algorithm、Review、Tip、Share 简称ARTS 

1.每周至少做一个 leetcode 的算法题 2.阅读并点评至少一篇英文技术文章 3.学习至少一个技术技巧 4.分享一篇有观点和思考的技术文章

# Algorithm

https://leetcode.com/problems/maximum-subarray/submissions/

最大连续子数组

```
func maxSubArray(nums []int) int {
    
    // 假设某个子数组和最大
    // 1. 那么该数组的第1位一定是大于0，否则除掉该数，剩余数组的和更大
    // 2. 同理数组的最后1位一定也大于0。
}
```

* 根据min size subarray的思路，brute force, 把全部结果放入一个map(k:i-j v:sums[i..j]) 得到一个"Memory Limit Exceeded"
```
// 遍历全部的组合[i..j],得到sums = map[start,end]sums, log(n2) 
// 遍历sums,取最小的一个即可
func maxSubArray(nums []int) int {
    m := make(map[string]int)
    for i := 0;i<len(nums);i++{
         sum := 0 // YC:初始化为nums[i] or 0
         j := i 
         for ;j<len(nums);j++{ // [0] [0+1] [0+1+2]
           sum += nums[j]
           m[strconv.Itoa(i)+"-"+strconv.Itoa(j)] = sum
         }
        
    }
    maxSumKey := "0-0"
    for k,v := range m{
        if v > m[maxSumKey]{
            maxSumKey = k
        }
    }
    return m[maxSumKey]
}
// test case
[-2,1,-3,4,-1,2,1,-5,4]
[1]
```
* 改进：并不需要多余的存储空间，移除m，使用maxSum存储最新的最大sum即可

```
// 不需要临时的存储m
func maxSubArray(nums []int) int {
    maxSum := 0
    for i := 0;i<len(nums);i++{
         sum := 0
         j := i
         for ;j<len(nums);j++{ // [0] [0+1] [0+1+2]
           sum += nums[j]
             if sum > maxSum{
                 maxSum = sum
             }
         }
    }
    return maxSum
}
// test case
[-2,1,-3,4,-1,2,1,-5,4]
[1]
[-1] // bug: 应该返回负数-1，而不是默认值0
```

* fix bug

```
// 不需要临时的存储m
func maxSubArray(nums []int) int {
    if len(nums) == 0 {
        return 0
    }
    maxSum := nums[0]
    for i := 0;i<len(nums);i++{
         sum := 0
         j := i
         for ;j<len(nums);j++{ // [0] [0+1] [0+1+2]
           sum += nums[j]
             if sum > maxSum{
                 maxSum = sum
             }
         }
    }
    return maxSum
}
```

* 应用

股票最大收益不是"低价买进，高价卖出"

http://yeziahehe.com/2017/09/21/MaximumSubArray/

# Review
https://medium.com/golangspec/detect-locks-passed-by-value-in-go-efb4ac9a3f2b


# Tip

* 【Golang】去除slice中重复的元素，认识空struct

https://www.jianshu.com/p/5430eebd715c

* 数据库设计，表名，用e和r表示实体和联系

* Golang range channel、close channel 遍历和关闭
https://blog.csdn.net/zhaominpro/article/details/77584534

方法一: for

方法二: range
然后会一直阻塞当前协程，如果在其他协程中调用了close(ch),那么就会跳出for range循环。`这也就是for range的特别之处`

https://stackoverflow.com/questions/52943450/go-routine-for-range-over-channels

* 扩展go sync.map的length和delete方法


*
go vet -composites=false

`call of getMapLength copies lock value: sync.Map contains sync.Mutex`

https://medium.com/golangspec/detect-locks-passed-by-value-in-go-efb4ac9a3f2b
https://studygolang.com/articles/9619

* Unmarshal

```
bool, for JSON booleans
float64, for JSON numbers
string, for JSON strings
[]interface{}, for JSON arrays
map[string]interface{}, for JSON objects
nil for JSON null
```

https://godoc.org/encoding/json#Unmarshal

* Partly JSON unmarshal into a map in Go

https://stackoverflow.com/questions/11066946/partly-json-unmarshal-into-a-map-in-go
https://play.golang.org/p/RJbPSgBY6gZ

* Mysql死锁引起的事务未回滚问题

> https://www.jianshu.com/p/c90aa25fe648
> https://docs.oracle.com/cd/E17952_01/mysql-5.7-en/innodb-parameters.html

* Transaction And Lock--事务中使用return会回滚事务吗？

> https://www.cnblogs.com/TeyGao/p/3522965.html

* golang的嵌套事务管理
https://www.jianshu.com/p/2a144332c3db

* validator
> https://github.com/go-playground/validator

# Share

## 订单状态转换，及其编码实现 [TODO] 已经上个公司框架slipper的processor处理原理

http://www.woshipm.com/pd/594751.html?winzoom=1
https://blog.csdn.net/yangstarss/article/details/80493464

[operator和processor组件],订单状态流转和对应的业务处理解耦
https://www.jianshu.com/p/fe292b15a06a

https://www.sohu.com/a/255500725_483392

