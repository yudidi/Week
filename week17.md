
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
> https://github.com/yudidi/Week/blob/master/week3.md#tips

# Tip

* 第三方的回调不及时,支付状态如何更改呢。
