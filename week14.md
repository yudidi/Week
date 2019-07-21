# Algorithm、Review、Tip、Share 简称ARTS
1.每周至少做一个 leetcode 的算法题 2.阅读并点评至少一篇英文技术文章 3.学习至少一个技术技巧 4.分享一篇有观点和思考的技术文章

# Algorithm
https://leetcode-cn.com/problems/maximum-subarray/

# Review

关于如何避免Merge Conflicts的几个建议。
1. feature分支和master分支应该 尽快合并
2. 只能从master切出feature分支，不能从feature分支切出feature分支
3. 把子分支合并到父分支，而不是把2个兄弟分支进行合并

> https://itnext.io/recommendations-to-avoid-merge-conflicts-845ec133676e

# Tip

* kibana 快速查询记录的上下100行

https://www.dgstack.cn/archives/2917.html

https://github.com/elastic/kibana/pull/9198

* MySQL索引及性能优化分析 三、explain执行计划
https://www.cnblogs.com/runtimeexception/p/10361099.html


* 多列索引 可以按照leftmost原则 替代单列索引

用简略地话来说，Unique Index的Index作用：1）当只有一个字段时，其Index作用也同样地施加到该字段上；2）当为多个字段的组合时，其Index的作用，只施加到组合的第一个字段上。

所谓差之毫厘，谬之千里。当待检索的字段是某个Unique Index的组合字段之一，且不是第一个时，被用做Where的查询条件，查询性能将急剧下降，每次皆是全表扫描，逐行对比。

这种性能隐患，在开发初期并不容易发现，只有当数据量级增长到10M+时，查询耗时才会逐步显现出来。
> https://ufqi.com/blog/sql-optimize-unique-and-index/
> https://dev.mysql.com/doc/refman/8.0/en/multiple-column-indexes.html

# Share

* 确定需求优先级：矩阵思维
http://www.woshipm.com/pmd/933370.html

* FAQ-产品经理对产品细节需要给出到什么程度，才不会被开发骂？

https://www.zhihu.com/question/48210161

* 业务相关

​互联网保险：模式、玩法和痛点、未来
http://www.woshipm.com/it/420819.html

* 软件开发和协作工具
https://www.baidu.com/s?wd=atlassian&rsv_spt=1&rsv_iqid=0xe48651bf00031e7b&issp=1&f=8&rsv_bp=1&rsv_idx=2&ie=utf-8&rqlang=cn&tn=baiduhome_pg&rsv_enter=1&rsv_t=8a6dhAOItPklLpmyCL7fdU96yjuycCq7kYtRaBWMl4sXh2K0WUpga88EKxib4%2FAfloWc&oq=atlassian&inputT=312&rsv_sug3=2&rsv_pq=8c63c8580003bb68&rsv_sug2=0&rsv_sug4=980
