
# mysql-insert-ignore [R2]

* However, if you use the INSERT IGNORE statement, 
the rows with invalid data that cause the error `are ignored` and the rows with valid data are inserted into the table.

* MySQL `truncated` data before inserting it into the tokens table

http://www.mysqltutorial.org/mysql-insert-ignore/


# “INSERT IGNORE” vs “INSERT … ON DUPLICATE KEY UPDATE”

I would recommend using INSERT...ON DUPLICATE KEY UPDATE.


> https://stackoverflow.com/questions/548541/insert-ignore-vs-insert-on-duplicate-key-update

# 在InnoDB中使用INSERT IGNORE来避免自动递增的漏洞

> https://www.oschina.net/question/207055_33444
