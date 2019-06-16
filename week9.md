# Algorithm、Review、Tip、Share 简称ARTS

1.每周至少做一个 leetcode 的算法题 2.阅读并点评至少一篇英文技术文章 3.学习至少一个技术技巧 4.分享一篇有观点和思考的技术文章

# Algorithm

https://leetcode.com/problems/remove-element/

# Review
目前在用流利说学习英语口语，英文文章阅读暂缓。

# Tip

* inner join PK left join
left join 会导致有缺列的左表数据被查询出来，进而导致bug。

1. inner join(内连接)： 只将2表中能关联起来的数据进行返回，每个表都可能丢弃几行记录。
2. left join(左外连接)： 左表的所有记录 * 右表中于左表关联的记录。 YC: 如果左表的连接字段为null,仍然会被取出，这也就制造了异常的数据。


* Json RawMessage
使用场景：某个字段是嵌套的结构体，并且这个结构体字段是不同的。有一个同级的字段用于表明类型，需要先解析这个字段才能解析嵌套的字段。

https://www.jianshu.com/p/c06666b8249c

# Share
自己动手写docker-Chapter 1:

Linux Namespace 是 Kernel 的一个功能，它可以隔离一系列的系统资源，比如 PIO (Process ID)、 User ID、 Network 等。 
