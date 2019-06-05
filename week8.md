Algorithm、Review、Tip、Share 简称ARTS

1.每周至少做一个 leetcode 的算法题 2.阅读并点评至少一篇英文技术文章 3.学习至少一个技术技巧 4.分享一篇有观点和思考的技术文章

# Algorithm


# Tip

## Q: 为什么很多框架中会有大量只有一条return语句的函数存在
源源不断的需求变更，迟早会把你当初还算满意的代码结构修改的面目全非，所以即便是一条简单的赋值语句，也最好把它封装在函数里吧。
因为你不知道什么时候来了一个需求会改变它。这样即便是反复的修改，也不会影响到主体代码结构的可读性。
也算是明白了，为什么很多框架中会有大量只有一条return语句的函数存在。

# Share

## context 专题



context的作用：
考虑有一个goroutine专门用于监控。
考虑从一个goroutine1中创建的多层嵌套的goroutine，我们需要取消所有的goroutine,如何做到取消以goroutine1作为树根的所有创建的goroutine。

https://github.com/developer-learning/reading-go/issues/191

https://www.flysnow.org/2017/05/12/go-in-action-go-context.html


## context的取消特性，导致的一些坑
https://zhuanlan.zhihu.com/p/34417106
