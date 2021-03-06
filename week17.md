
# Algrithm

* 题意
最短的连续子数组

* 优化： 滑动窗口

> 接https://github.com/yudidi/Week/blob/master/week15.md#algorithm

https://leetcode.com/problems/minimum-size-subarray-sum/


* 
```
// 2. remove insureCodesToHide from tmp.List
	for i := 0; i < len(tmp.List); i++ {
		for j, hide := range insureCodesToHide {
			if tmp.List[i].InsureCode == hide {
				tmp.List = append(tmp.List[:i], tmp.List[i+1:]...)
				insureCodesToHide = append(insureCodesToHide[:j], insureCodesToHide[j+1:]...)
				i--  // YC: 如果没有这个，那么i之前的元素无法被删除。 [1，2，3] 删除 [1,2,3]
				break
			}
		}
	}
```

* 优化为，每趟删除一个hide元素
```
for _, hide := range insureCodesToHide { // 每趟删除一个hide元素
	for i, v := range tmp.List {
		if v.InsureCode == hide {
			tmp.List = append(tmp.List[:i], tmp.List[i+1:]...)
			break
		}
	}
}
```

> https://github.com/yudidi/Week/blob/master/week3.md#tips


## 暴力解法和标准解法不一致，3层循环和2层循环均可以罗列全部子数组

`YC:没有进行剪枝操作`

https://leetcode.com/problems/minimum-size-subarray-sum/solution/

```
// 2层循环枚举全部情况
func minSubArrayLen(s int, nums []int) int {
	minLen := len(nums) + 1
	for i, _ := range nums { // 每趟都寻找i开头的最短子数组
		sum := 0 
		for j := i; j < len(nums); j++ {
			sum += nums[j] // [0] [0,1] [0,1,2] // [1] [1,2]
			fmt.Println(i,j,sum)
			if sum >= s {
				if (j - i + 1) < minLen { // j-i+1,[i..j]的数组长度
					minLen = j - i + 1
					break // YW: 剪枝
				}
			}
		}
	}
	return minLen
}

// 3层循环，比较易懂
func minSubArrayLen(s int, nums []int) int {
	n := len(nums)
	minLen := n + 1
	for i, _ := range nums { // 选子数组起点i
		for j := i; j < n; j++ { // 选子数组终点j
			sum := 0
			for k := i; k <= j; k++ { // 子数组[i..j]求和
				sum += nums[k]
			}
			fmt.Println(i, j, sum)
			if sum >= s {
				if (j - i + 1) < minLen { // j-i+1,[i..j]的数组长度
					minLen = j - i + 1
					 break  
					 // YW: Found the smallest subarray with sum>=s starting with index i, hence move to next index
					 // 此时子数组是第一个满足的子数组，也是最短的。因为是寻找最短子数组，如果不break继续j++,那么之后找到更长的子数组				}
			}
		}
	}
	return minLen
}

```

> https://play.golang.org/p/f7a7UCAD0mn
> https://play.golang.org/p/LFqPPV9d8n7

# Tip

* Q: 第三方的回调不及时，导致订单的支付状态，在我方和第三方的状态不一致,支付状态如何更改呢。

A: 考虑在待支付和已支付，增加一个中间状态, 正在支付？TODO

A: 需要第三方提供查询接口，用于查询订单状态


* 常见的支付流程


* 需求做到后面，越来越多的需求开始交叉影响，导致新需求越做越慢。

* 爬虫：混淆加密代码的破解

https://blog.csdn.net/qian123shuai/article/details/84197652

# Share

* 软件项目为什么越做越慢？ - 知乎

> https://www.google.com/search?ei=p4xKXYnwC5X1-gTJtaHgDg&q=%E6%96%B0%E9%9C%80%E6%B1%82%E8%B6%8A%E5%81%9A%E8%B6%8A%E6%85%A2+%E8%BD%AF%E4%BB%B6%E5%BC%80%E5%8F%91&oq=%E6%96%B0%E9%9C%80%E6%B1%82%E8%B6%8A%E5%81%9A%E8%B6%8A%E6%85%A2+%E8%BD%AF%E4%BB%B6%E5%BC%80%E5%8F%91&gs_l=psy-ab.3...12292.14322..14516...0.0..1.678.2393.3-2j1j2......0....1..gws-wiz.GnzfuIEeFV8&ved=&uact=5

> https://36kr.com/p/5130526

* 优秀的开发文档写作思路 - 微信支付文档

https://pay.weixin.qq.com/wiki/doc/api/jsapi.php?chapter=23_6&index=4

* nginx 的转发过程。

# 业务

* 如何看待人民币汇率破七，你有什么想法？



