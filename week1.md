Algorithm、Review、Tip、Share 简称ARTS

1.每周至少做一个 leetcode 的算法题
2.阅读并点评至少一篇英文技术文章
3.学习至少一个技术技巧
4.分享一篇有观点和思考的技术文章

# Algorithm
https://leetcode.com/problems/move-zeroes/

代码在leetcode网站可查。主要记思路。
```
/*
[01,02,1]-[02,01,1]-[02,1,01]
*/
func moveZeroes(nums []int)  {
    n := len(nums)
    for i:= 0;i< n-1;i++{ // [0,n-2] (n-1) times  // i<2
        
        for j:=0;j<n-1-i;j++ { // j: [0,j] is not handled. 
            
            if nums[j] == 0 && nums[j+1] != 0{ // j<2 
                nums[j],nums[j+1] =  nums[j+1],nums[j] 
            }
        }
    }
    fmt.Println(nums)
}
```

### 如何想到的
1. 举例子，进行试运行 [01,02,1]-[02,01,1]-[02,1,01]
2. 发现和冒泡的思路有点类似，
冒泡：每趟把max冒泡至末尾，然后再对剩余对数组继续冒泡，这样冒泡n-1躺，就可以完成升序排序。  由于是顺次交换，所以是稳定排序。
借鉴：每次把1个0冒泡至末尾，然后对剩余数组的0进行冒泡，这样冒泡n-1躺，就可以把所有0放在最后。顺次交换，稳定排序。

### 再次检查题目限制条件
要求稳定排序,in-place. 满足

* 扩展：交换和稳定性的关系
稳定排序：顺次交换
不稳定排序：交换

### 复杂度
时间复杂度：O(n2)

TODO: 看一下leecode上别人更好的解法

# Review
https://blog.golang.org/using-go-modules
* 主题：GO官网的一篇指导Gopher使用go-moudles的教程类技术文章。(Go 1.11+)
* 阅读目的：学习写作教程类文章的写作思路，常用词汇
* 点评：
1. 首先给出整个文章的写作概要，便于读者迅速把我主题内容和行文思路。
2. 结合实例进行讲解。注意每一步关键点，都有讲解，确实是娓娓道来，对新手非常友好。

# Tip
**MySql避免重复插入记录方法(ignore,Replace,ON DUPLICATE KEY UPDATE)**

1. 案一：使用ignore关键字
如果是用主键primary或者唯一索引unique区分了记录的唯一性,避免重复插入记录可以使用：


2. 方案二：使用Replace
根据主键或唯一关键字，检测到重复时，先删除旧行，再插入新到一行，所以id会变化。
PS: 因为id可能被其他业务依赖，如此会导致问题，所以MYSQL不要用REPLACE，https://yq.aliyun.com/articles/627744

3. 方案三：ON DUPLICATE KEY UPDATE

> referece

http://blog.sae.sina.com.cn/archives/3491

http://www.mysqltutorial.org/mysql-insert-or-update-on-duplicate-key-update/


# Share
Using Service Objects in Go: https://itnext.io/using-service-objects-in-go-d899dc599335
* 主题：好像是说，这么写的代码符合SRP单一职责原则，能够更好对应对需求变化。 TODO 没有get到，但是感觉很吊，有6赞

> 从CODE REVIEW 谈如何做技术 : https://coolshell.cn/articles/11432.html


