
# Algrithm

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
