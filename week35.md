# Algorithm

## 数组删除操作的性能优化和实际应用案例

* 删除：数组大小为n，将第k个位置数据删除，需要将k~n位置数据均向前移动一位，平均时间复杂度为O(n)。

对于数据连续性要求低的情况，可以将多个删除操作集中到一次进行，
被删除的数据标记删除，`新数据`(Q:哪来的)从数组尾部扩展`，直到数组没有空间，将标记删除的数据一次性清除(Q:怎么一次性删除?)，`其余数据一次性前移相应位数`。

动画示意图: https://user-gold-cdn.xitu.io/2019/9/9/16d138d1c9a87e55?imageslim

> https://www.lt-tree.com/2019/06/20/%E6%95%B0%E6%8D%AE%E7%BB%93%E6%9E%84%E4%B8%8E%E7%AE%97%E6%B3%95%E4%B9%8B%E7%BE%8E1_%E6%95%B0%E7%BB%84&%E9%93%BE%E8%A1%A8/

* 这个思想应用非常广泛:

```
前端框架的虚拟DOM就是将对DOM的大量操作先储存在差异队列中,然后再一次性更新,避免了DOM的回流和重绘.
V8和JVM中的标记清除算法也是基于此思想,标记清除算法分为两个阶段,标记阶段对访问到的对象都打上一个标识,在清除阶段发现某个对象没有标记则进行回收.
```
> https://juejin.im/post/5d75a5266fb9a06b1a56b137#heading-9

# 链表
## 206. Reverse Linked List
```
//      1->2->3->null
//null<-1<-2<-3
// cur:当前处理的节点,cur.Next需要指向其前一个元素
// next:保存子链
// pre:保存前一个元素
// 
// Test Cases: 1. NULL 2.One Node 3. Two Nodes
func reverseList(head *ListNode) *ListNode {
    var pre *ListNode 
    cur := head
    for cur != nil{
        next := cur.Next // save next
        cur.Next = pre // recerse cur
        // update pointers for next iterate
        pre = cur
        cur = next
    }
    return pre
}
```
> https://leetcode.com/problems/reverse-linked-list/

# Go Interview QA

## schedule

## interface

# 定语从句——介词＋which如何快速理解？
为此，我们总结出一套3步处理“介词＋which”定语从句的方法：替换，带入，在一起。
> http://www.360doc.com/content/18/0213/10/50323900_729728014.shtml
