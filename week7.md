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
func sumOfLeftLeaves(root *TreeNode) int {
    if root == nil{
        return 0
    }
    return dfs(root,false)
}

// 求root为根的树的左叶子节点的和
// root: 子树的根节点
// isLeft: 是否是左子树的根节点，只有这种情况才能是左叶子节点。
func dfs(root *TreeNode,isLeft bool) int { // 模拟运行:root是 1节点，3节点，5节点
    if root == nil{
        return 0
    }
    // 节点类型判断：要么是叶子节点，要么是非叶子节点。 叶子节点又分为左叶子和右叶子。 
    if root.Left == nil && root.Right == nil && isLeft { // 左叶子
         return root.Val
    } else {  // 右叶子 + 非叶子
        return dfs(root.Left,true) + dfs(root.Right,false)
    }
}

// 关键: 
// 1. 叶子节点的判断：root.Left == nil && root.Right == nil 
// 2. 左右叶子的判断: isLeft

// 思路：本题是求左叶子节点的和，肯定要遍历左叶子节点。 1. 先思考遍历叶子节点 -> 2. 思考遍历全部节点 -> 3+1. 遍历全部
// 节点+ 如何判断是叶子节点 -> 4. 找到了叶子节点后，又如何判断是左叶子节点 -> 5. 递归函数中如何累计求和。

// Q: 为什么不需要传递一个sum值，用于存放累加的结果。
// A：考虑到递归函数的执行过程，函数会一层层返回，每个函数把左叶子节点的值返回给上一个调用函数即可。
// A：这和递归函数是栈结构没有关系，不要把因果关系搞混了，是因为需要一层层返回，所以才选的栈，作为函数调用关系的存储结构
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


