

# mysql LIKE的字符串拼接

```
SELECT xxxx FROM t
WHERE
 is_displayed = TRUE AND case_code LIKE ? [%7%]
 ```

# mysql字段为NULL和golang结构体字段为json.RawMessage

1. NULL字段反射到json.RawMessage会导致panic，只能反射到string [R2]
2. 数据库预编译语句的?遇到nil指针时,会被转换为NULL。

```
if userCode == "" {
			userId = nil
		} else {
			userId = userCode
		}
		if _, err = this.dao.conn.Insert(
			"INSERT xxxx (user_id) VALUES(?)", // 相当于 VALUES(NULL)
			userId,
		)
```
