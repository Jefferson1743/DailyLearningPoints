# SQL调优

## 基本原则


## Join
### 驱动表和被驱动表的定义
+ 驱动表：外层嵌套循环，尽量能够一次IO读取所有的数据
+ 被驱动表：内层嵌套循环，每次与驱动表的一条数据进行循环匹配

区别：
+ 驱动表适合顺序读取。数据量过大，且没有索引适合
+ 被驱动表适合随机读取
### 驱动表和被驱动的示例
- left join：左表是驱动表，右表是被驱动表
- right join：右表是驱动表，左表是被驱动表
- inner join：数据量较小的是驱动表
- 存在where条件，会根据实际条件选择小表驱动大表

### 查询方式
+ Simple Nested-Loop Join
首先读取驱动表中，每次顺序选取驱动表中的一条数据与被驱动表中的数据进行匹配。

[Simple Nested-Loop Join ](./.img/simpleNestedLoopJoin.png)


+ Index Nested-Loop Join

如果on的字段有索引，会优先选择开销小的表作为驱动表。
如果还存在where限制条件，可以进一步减少开销。
[Simple Nested-Loop Join ](./.img/indexNestedLoopJoin.png)

+ Block Nested-Loop Join

查询不会直接使用 simple Nested-Loop Join，会先使用Block Nested-Loop Join。
批量加载驱动表的数据，与被驱动表进行匹配。
[Simple Nested-Loop Join ](./.img/blockNestedLoopJoin.png)
