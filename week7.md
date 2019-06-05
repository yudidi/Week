Algorithm、Review、Tip、Share 简称ARTS

1.每周至少做一个 leetcode 的算法题 2.阅读并点评至少一篇英文技术文章 3.学习至少一个技术技巧 4.分享一篇有观点和思考的技术文章

# Algorithm

https://leetcode.com/problems/sum-of-left-leaves/

* 思路容易有，但是不好实现。

遍历所有节点，判断是否是左叶子节点，如果是则放入累加值中。

难点：具体编程实现。

* 如何想到的

1. 遍历左叶子节点 -> 2.遍历二叉树的叶子节点(dfs) -> 3. 遍历二叉树的所有节点 
-> 2. 在二叉树的遍历算法基础上增加检测结点的“左右子树是否都为空”,用于判断是否为叶子节点 -> 1. 如何判断是左叶子节点，传入一个标记，表明是左还是右。

```
```

TODO：用递归和非递归

借鉴:
https://blog.csdn.net/mebiuw/article/details/52664346?_t=t

# Review
目前在用流利说学习英语口语，英文文章阅读暂缓。

# Tip 

TODO golang
1. Map，slice 参数传递
2. map 并发 https://github.com/yudidi/Week/blob/master/week6.md#tip

* sql查找一列中某一数值出现次数大于2的记录
https://zhidao.baidu.com/question/1883519508681617748.html


* 面试-场景设计题，结合工作中的小需求

订单10分钟未支付的提醒

xxx提醒

* mysql 计算两个时间之间有多少分钟

https://blog.csdn.net/qq_33335927/article/details/82422530


## golang,timeout: context or select

适用场景不同

* context

一个ctx可以被多个函数共用便于统一管理

不然你要修改一下延迟时间还得一个一个改

http://jgao.io/?p=7


* select

* select+time.After的方式的弊端

 `time.After()`
 `time.NewTimer`

https://studygolang.com/articles/1882


* golang.org/x/image/math/fixed 下载


# Share

go context应用场景

https://www.jianshu.com/p/6def5063c1eb


