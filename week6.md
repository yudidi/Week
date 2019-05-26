
Algorithm、Review、Tip、Share 简称ARTS

1.每周至少做一个 leetcode 的算法题 2.阅读并点评至少一篇英文技术文章 3.学习至少一个技术技巧 4.分享一篇有观点和思考的技术文章

# Algorithm
https://leetcode.com/problems/two-sum-iv-input-is-a-bst/

* 如何想到的
根据之前对two sum的思路。有2层循环暴力求解 || 查找表 || 双指针对撞 三个思路。

发现思路3走不通，因为BST做不到像有序数组那样使用2个指针进行搜索，所以使用思路2:查找表进行处理。

// 以下代码不对

```
/**
 * Definition for a binary tree node.
 * type TreeNode struct {
 *     Val int
 *     Left *TreeNode
 *     Right *TreeNode
 * }
 */
 
func findTarget(root *TreeNode, k int) bool {
    // 仍然可以使用查找表进行处理.
    set := make(map[int]bool) // 存入已经遍历过的元素// 一遍遍历，一边往查找表放入值
    return helper(root.Left,k,set) || helper(root.Right,k,set) // Warning: root节点不会被处理。
}

// check if set has k-r.
func helper(cur *TreeNode,k int,set map[int]bool) bool{
    if cur.Left == nil || cur.Right == nil { // Error: 边界判断有问题，叶子节点在这种情况处理不到.
        return false
    }
    if _,ok := set[k-cur.Val];ok{
        return true
    }else{
        set[cur.Val] = true
    }
    return helper(cur.Left,k,set) || helper(cur.Right,k,set)
}
```

* 不对的原因

```
// 1. Error: 边界判断有问题，导致叶子节点不会被处理到
if cur.Left == nil || cur.Right == nil { 

// 2. Warning: root节点不会被处理。
return helper(root.Left,k,set) || helper(root.Right,k,set) 
```

* 修改后通过

```
func findTarget(root *TreeNode, k int) bool {
    // 仍然可以使用查找表进行处理.
    set := make(map[int]bool) // 存入已经遍历过的元素// 一遍遍历，一边往查找表放入值
    return helper(root,k,set)
}

// check if set has k-r.
func helper(cur *TreeNode,k int,set map[int]bool) bool{
    if cur == nil {
        return false
    }
    if _,ok := set[k-cur.Val];ok{
        return true
    }
    set[cur.Val] = true
    return helper(cur.Left,k,set) || helper(cur.Right,k,set)
}
```

总结：递归函数，易错点：递归逻辑，边界判断。

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
* Golang库集合

https://www.jianshu.com/p/6a147fc00721

Gods - Go 语言数据结构、容器、集合、列表、栈、键值对、 BidiMaps、树、HashSet 等

Golang-set - 线程安全和非线程安全的高性能集合
