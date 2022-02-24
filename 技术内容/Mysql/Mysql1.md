# Mysql基础知识
## 常见关键字

### 使用数据库
+ SHOW

```SQL
查询数据库操作：
    SHOW DATABASES;
    SHOW TABLES;
    SHOW COLUMNS FROM TAB_NAME;
    SHOW CREATE DATABASE；
    SHOW CREATE TABLE；

查询数据库的状态：
    SHOW STATUS；
    SHOW ERRORS；
    SHOW WARNINGS；
    SHOW GRANTS；
```
### 查询

+ SELECT

    - 通配符（*）：查询所有的列。
    - DISTINCT：对查询结果去重操作。使用必须放在所有列的前面，作用于所有列。
    - LIMIT INDEX，SIZE：限制查询结果的容量，返回第(INDEX)至(INDEX+SIZE)条。
```SQL
查询字段信息：
    SELECT COL_NAME FROM TAB_NAME;
    SELECT * FROM TAB_NAME; // * 是通配符，返回数据包括所有字段
    SELECT DISTINCT COL_NAME1, COL_NAME2 FROM TAB_NAME; // DISTINCT是去重操作(作用域必须是所有查询列)
```
+ limit
+ 