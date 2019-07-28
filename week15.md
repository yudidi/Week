Algorithm、Review、Tip、Share 简称ARTS
1.每周至少做一个 leetcode 的算法题 2.阅读并点评至少一篇英文技术文章 3.学习至少一个技术技巧 4.分享一篇有观点和思考的技术文章


# Algorithm
https://leetcode.com/problems/maximum-subarray/

```

```

* 应用

1. 股票最大收益不是"低价买进，高价卖出"
http://yeziahehe.com/2017/09/21/MaximumSubArray/ Subarray

# Tip

* Q: 哪些业务接口必须100%覆盖测试
A1: 基础数据类的接口
1. 用户信息/家庭成员
2. 保险产品
3. 保单

A2: 其他在基础数据上衍生的接口，不必覆盖测试
1. 筛选功能
2. 推荐功能
3. 风险测评

* 修改基础数据相关表时，需要明确哪些业务用到了该表，注意修改。

## sql语句编写时，需要考虑是否能使用索引

```
SELECT * FROM product_search_relation WHERE ( query_type, query_value, is_recommend ) IN ((?,?,TRUE),(?,?,TRUE),(?,?,TRUE));

//
SELECT * FROM product_search_relation WHERE query_type = ? AND query_value = ? AND is_recommend = TRUE
UNION
SELECT * FROM product_search_relation WHERE query_type = ? AND query_value = ? AND is_recommend = TRUE
UNION
SELECT * FROM product_search_relation WHERE query_type = ? AND query_value = ? AND is_recommend = TRUE`
```

## panic导致事务没有结束，导致死锁

## 旧的公共接口不能随便该，尤其是没有完整测试的情况下。会出现异常情况。
家庭成员add和update接口修改。
旧接口不能随便该，尤其是没有完整测试的情况下。会出现异常情况。

## map的key如果是interface，是什么意思

```
var sexMapping = map[interface{}]int64{
	1:   1,
	2:   2,
	"1": 1,
	"2": 2,
}

func main() {
	var i interface{}
	i = 1
	fmt.Println(sexMapping[i])
	i = "1"
	fmt.Println(sexMapping[i])
}

```

你的map里的key 1的默认类型是int
`如果定义一个interface的变量k, sexMapping[k]是匹配不到值的，因为map匹配要求key的类型和值都相同才能匹配`

## 记Golang switch的一个“坑”
golang  switch 默认给每个case都加了break
https://blog.csdn.net/Coder_MA/article/details/81434834


## 团队士气管理

一个项目延期太多，导致士气下降。
