# Algorithm、Review、Tip、Share 简称ARTS
1.每周至少做一个 leetcode 的算法题 2.阅读并点评至少一篇英文技术文章 3.学习至少一个技术技巧 4.分享一篇有观点和思考的技术文章

# Algorithm

https://leetcode.com/problems/remove-element/

* 怎么想到的

双指针，一个用来标记结果数组，一个用于挑选元素放入结果数组中。

编程体现：[0,i]表示结果数组，j指针用于挑选元素，不断的放到i位置，然后结果数组扩展1位。
如此循环，直到j到达数组末尾，挑选完毕。此时[0,i]就是结果数组。

```
// 3,2,2,3 // i:指向结果数组  j:用于挑选元素，添加到结果数组中。
// YC：初始化
func removeElement(nums []int, val int) int {
    i := 0 // [0,i] 结果数组，起始没有元素 
    for j:=0 ;j<len(nums);j++{
        if nums[j] != val{
            nums[i] = nums[j]
            i++
        }
    }
    return i
}
```

# Review
目前在用流利说学习英语口语，英文文章阅读暂缓

# Tip

# Share

Q：你知道哪些数据结构可以提高查询速度？

A：哈希表、完全平衡二叉搜索树、B树、B+树等等；

Q：那这些数据结构既然都能优化查询速度，那MySQL为何选择使用B+树？ 
https://www.cnblogs.com/blogtech/p/10530794.html

* 分析思路：选择数据结构的思路

`我们考虑关系型数据库的一个表，然后需要进行查询`

A1：（1）哈希表的特点
因为哈希表的特点就是可以快速的精确查询，但是不支持范围查询！
```
select * from users where name = '周瑜'; // 可以实现
select * from users where name > '周瑜'; // 实现不了
```

A2:（2）完全平衡二叉搜索树

A3:（3）B树



