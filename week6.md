
Algorithm、Review、Tip、Share 简称ARTS

1.每周至少做一个 leetcode 的算法题 2.阅读并点评至少一篇英文技术文章 3.学习至少一个技术技巧 4.分享一篇有观点和思考的技术文章

# Algorithm
https://leetcode.com/problems/two-sum-iv-input-is-a-bst/

* 如何想到的
根据之前对two sum的思路。有2层循环暴力求解 || 查找表 || 双指针对撞 三个思路。
发现第三个思路走不通，因为BST做不到像有序数组那样使用2个指针进行搜索，所以使用查找表进行处理。



# Review
目前在用流利说学习英语口语，英文文章阅读暂缓。

# Tip

* 删除包含某字符串的一整行

`.*ER_.*`,匹配某字符串所在的一行

https://blog.csdn.net/Touatou/article/details/83380364

* map 并发读，并发写，并发读写

https://www.cnblogs.com/qcrao-2018/archive/2019/05/22/10903807.html

Q: sync.Map的使用
https://www.jianshu.com/p/3956267e29cd

TODO: 使用channel通信来保证2个go任务都完成了，最优雅.

* goroutine并发通信

在工程上，有两种最常见的并发通信模型：共享数据 和 消息。

https://blog.csdn.net/wo18237095579/article/details/81909189

=> channel 不要通过共享内存来通信，而应该通过通信来共享内存。

https://blog.csdn.net/wo18237095579/article/details/81912653

* 有无缓冲的channel.


# Share
Golang库集合
https://www.jianshu.com/p/6a147fc00721
Gods - Go 语言数据结构、容器、集合、列表、栈、键值对、 BidiMaps、树、HashSet 等
Golang-set - 线程安全和非线程安全的高性能集合
