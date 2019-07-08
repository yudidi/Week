
# Algorithm、Review、Tip、Share 简称ARTS

1.每周至少做一个 leetcode 的算法题 2.阅读并点评至少一篇英文技术文章 3.学习至少一个技术技巧 4.分享一篇有观点和思考的技术文章


# Tip 

## 数据库库设计

除非不得已，不要设计拼接的字符串，而是利用关系型数据库的本身的性质。用于关系表存储，而不是拼接的方式进行存储。

四种设计方案：

1. 关系表：产品id+搜索条件
2. 关系表：搜索条件+产品ID

* bug修改问题. Code Review.

去重问题
1. 有序数组去重
2. 无序数组去重
3. 删除数组中元素，下标的联动变化问题

一个典型的无序数组去重问题。 > https://git.lcgc.work/insurance/service/merge_requests/353/diffs

```
for _, r := range response.List {
		for j := 0; j < len(r.Products)-1; j++ {
			cur := r.Products[j]
			for k := j + 1; k < len(r.Products); k++ {
				if cur.ProductId == r.Products[k].ProductId {
					if cur.InsuranceType > r.Products[k].InsuranceType {
						response.List[j].Products = append(r.Products[:j], r.Products[j+1:]...)
					} else {
						response.List[j].Products = append(r.Products[:k], r.Products[k+1:]...)
					}
					break
				}
			}
		}

```


# Share

https://blog.csdn.net/basonson/article/details/50924466
