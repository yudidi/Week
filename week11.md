
# Algorithm、Review、Tip、Share 简称ARTS
1.每周至少做一个 leetcode 的算法题 2.阅读并点评至少一篇英文技术文章 3.学习至少一个技术技巧 4.分享一篇有观点和思考的技术文章

# Algorithm

https://leetcode.com/problems/remove-element/

* 解法1总结：就是遍历所有元素，然后把需要保留的元素，Copy到结果数组中，如果是需要删除的元素，则不进行Copy，最后结果数组中都是需要保留的元素了。

如果需要删除的元素很少，我其实并不需要Copy那么多次。
比如`nums=[1,2,3,5,4],val=4`,前4个元素的copy可以想办法去掉 和 `nums=[4,1,2,3,5],val=4`，

* Approach 2: Two Pointers - when elements to remove are rare.

算法：When we encounter nums[i] = val, we can `swap the current element out with the last element and dispose the last one`. This essentially reduces the array's size by 1.

```
func removeElement(nums []int, val int) int {
    // if nums[i] == val, swapped it with the last one and drop the last one.
    // This essentially reduces the array's size by 1.
    
    // So the size of array is change,we can use 'for',and should use 'while'
    i := 0
    n := len(nums)
    for ;i<n;{
        if nums[i] == val{
            nums[i],nums[n-1] = nums[n-1],nums[i]
            n--
        }else{
            i++
        }
    }
    return n
}
```

* golang删除slice中特定条件的元素，优化版

https://blog.csdn.net/liyunlong41/article/details/85132603

# Tip
mysql中数据类型的取值范围
https://www.cnblogs.com/web21/p/6016120.html


Golang神奇的2006-01-02 15:04:05

https://www.jianshu.com/p/c7f7fbb16932


linux内核架构

https://www.cnblogs.com/holyxp/p/9760084.html

linux面试

```
一.内核5大子模块 
 1.内存管理、
 2.进程调度、
 3.进程间通信、
 4.网络接口
 5.文件系统。
目标：
    看到syscall那层知道各自api怎么用，
    基础里面知道名词，理解名词对应的原理
    做遍clfs，然后看懂各个module关系
收益比高的方法：
    vfs上层 net上层，学习bcc systemtap等
*有句话，了解完ioctl各种参数使用和细节，内核基本会了一半
```


* golang json

`json:"-" column:"detail"`

* golang reflect

 reflect: call of reflect.Value.Set on zero Value
 
 
 * MySql - 快速执行：在update时使用select赋值
 
```
UPDATE disease_question T1,disease_question T2 SET T2.rank= T1.id  WHERE T1.rank = 127 ANd T1.id = T2.id
```
 https://blog.csdn.net/qq_15071263/article/details/79001487
 
 
 * mysql 字段 is not null 和 字段 !=null
 https://blog.csdn.net/wangzaza/article/details/79484069
 

