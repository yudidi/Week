# Algorithm、Review、Tip、Share 简称ARTS

1.每周至少做一个 leetcode 的算法题 2.阅读并点评至少一篇英文技术文章 3.学习至少一个技术技巧 4.分享一篇有观点和思考的技术文章


# Algorithm

https://leetcode.com/problems/reverse-integer/


# Tip

Q: 判断数据是否存在，多个插入请求同时发生时，导致插入多组相同数据。

```
1. check
2. insert multiple
3. commit
```
A: 接口的幂等性.
如何防止重复提交数据，导致出现重复数据。
