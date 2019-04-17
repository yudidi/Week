Algorithm、Review、Tip、Share 简称ARTS

1.每周至少做一个 leetcode 的算法题
2.阅读并点评至少一篇英文技术文章
3.学习至少一个技术技巧
4.分享一篇有观点和思考的技术文章

# Tip
**MySql避免重复插入记录方法(ignore,Replace,ON DUPLICATE KEY UPDATE)**

1. 案一：使用ignore关键字
如果是用主键primary或者唯一索引unique区分了记录的唯一性,避免重复插入记录可以使用：


2. 方案二：使用Replace
根据主键或唯一关键字，检测到重复时，先删除旧行，再插入新到一行，所以id会变化。
PS: 因为id可能被其他业务依赖，如此会导致问题，所以MYSQL不要用REPLACE，https://yq.aliyun.com/articles/627744

3. 方案三：ON DUPLICATE KEY UPDATE

* referece
http://blog.sae.sina.com.cn/archives/3491
http://www.mysqltutorial.org/mysql-insert-or-update-on-duplicate-key-update/
