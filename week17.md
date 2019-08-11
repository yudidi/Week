
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



