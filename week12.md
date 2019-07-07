# Algorithm、Review、Tip、Share 简称ARTS

1.每周至少做一个 leetcode 的算法题 2.阅读并点评至少一篇英文技术文章 3.学习至少一个技术技巧 4.分享一篇有观点和思考的技术文章


# Algorithm

https://leetcode.com/problems/reverse-integer/

思路1：符号不变，数字逆序即可，同时判断一些越界。

官方思路2：逆序，借助额外的栈(先进后出) 实现数字逆序 + 边界判断(不同语言方法不同)。
进一步：使用数学方法实现顺序找出数字和逆序找出数字
> 或者 https://studygolang.com/articles/13289

思路3: 纯粹使用字符串逆序的方法来实现反转。
> https://blog.csdn.net/wangguoyang429883793/article/details/72904589

```

func reverse(x int) int {
    max := int(math.Pow(2,31) - 1)
    _x := int(math.Abs(float64(x)))
    s := strconv.Itoa(_x) 
    s = res(s)
    res,_:=strconv.Atoi(s)
    if res > max { // 越界
        return 0
    }
    if x > 0 { // 正数
        return res
    }
    return -res
}

func res(s string) string {
    len := len(s)
    res := ""
    for i := len - 1; i >= 0 ; i-- {
        res += string(s[i])
    }
    return res
}
```

* 几个知识点
1. 32位无符号数最大值: int(math.Pow(2,31) - 1)
2. 

# Tip

Q: 并发请求导致，插入重复数据

判断数据是否存在，多个插入请求同时发生时，导致插入多组相同数据。

```
// 并发请求1
1. check 
2. 执行多个表的数据插入操作。
3. commit

// 并发请求2
1. check
2. 执行多个表的数据插入操作。
3. commit

// 出现问题的步骤: 同时通过第一步check校验，然后会同时执行第2步的插入操作，导致插入了重复的数据到多个表之中。
```

A: 接口的幂等性.
如何防止重复提交数据，导致出现重复数据。

> 高并发下接口幂等性解决方案

https://blog.csdn.net/u011635492/article/details/81058153

* MySQL字段属性应该尽量设置为NOT NULL
https://www.cnblogs.com/liaokaichang/p/7879010.html


* golang性能分析

https://github.com/wangyaofenghist/ARTS/blob/master/Share/golang-work-pool-careful.adoc

