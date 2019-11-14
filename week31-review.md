
# golang默认数据类型

值的默认数据类型int,但是比较时的类型int64，导致map的reflect.DeepEqual失败


[R2] map里的key1的默认类型是int, 但是map匹配要求key的类型和值都相同才能匹配，导致key不匹配。

> https://github.com/yudidi/Week/blob/master/week15.md#map%E7%9A%84key%E5%A6%82%E6%9E%9C%E6%98%AFinterface%E6%98%AF%E4%BB%80%E4%B9%88%E6%84%8F%E6%80%9D 

# 定语和状语

## 定语和状语的概念是怎么出现的

句子中除了五大基本句型的组成部分，还多出了一部分，这些就是定语或状语

## 定语从句和状语从句的区别

* 定语，就是限定和或修饰名词、代词用的。

* 状语，就是用来修饰动词、形容词、副词或者是整个句子的。

> https://zhidao.baidu.com/question/585627796724291645.html

* Q: in which为什么能代替where，还有什么of which之类的为什么能被替换?

定语从句中的关系词分为两类：关系代词和关系副词。

> https://www.zhihu.com/question/342549456/answer/804129411


# golang

* reflect: call of reflect.Value.Set on zero Value

当字段是NULL或者""空时，都会导致反射问题

```
diagnosis := []*struct {
		Id               int64           `json:"id"`
		DiagnosisContent json.RawMessage `json:"diagnosis_content"`
	}{}
if err := this.conn.Query(
			&diagnosis,
			`SELECT id,diagnosis_content FROM insure_family_member`+memberIdsIn.Sql(),
			memberIdsIn.Bind()...,
		); err != nil {
			return http.STATUS_ERROR_DB
		}
```

* mysql设置text字段为not null，并且没有默认值，插入报错：doesn't have a default value

2、如果字段为text,则既不需要设置not null,也不需要手动设置default 的值

> https://blog.csdn.net/LJFPHP/article/details/81939189


# 业务架构设计

* 有多少人在滥用 service+serviceImpl，又有多少人在误用myBatis
https://www.iteye.com/blog/linsky328-2408997

* DO、DTO和VO分层设计的好处
https://www.cnblogs.com/yueguanguanyun/p/9355746.html
