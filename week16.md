



https://leetcode.com/problems/maximum-subarray/submissions/


```
func maxSubArray(nums []int) int {
    
    // 假设某个子数组和最大
    // 1. 那么该数组的第1位一定是大于0，否则除掉该数，剩余数组的和更大
    // 2. 同理数组的最后1位一定也大于0。
}
```

* 应用

股票最大收益不是"低价买进，高价卖出"

http://yeziahehe.com/2017/09/21/MaximumSubArray/



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


# Share

## 订单状态转换，及其编码实现

http://www.woshipm.com/pd/594751.html?winzoom=1
https://blog.csdn.net/yangstarss/article/details/80493464

[operator和processor组件],订单状态流转和对应的业务处理解耦
https://www.jianshu.com/p/fe292b15a06a

https://www.sohu.com/a/255500725_483392

