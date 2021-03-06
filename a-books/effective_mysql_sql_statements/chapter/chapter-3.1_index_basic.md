# 索引原理

* [示例表](https://github.com/effectiveMySQL/OptimizingSQLStatements/blob/master/sql/chapter03.sql)

## 索引用法
* 索引作用
```md
* 优化数据访问
* 保持数据完整性
* 改进表的join操作
* 对结果集排序
* 简化聚合数据操作
```
* 数据完整性
```md
主键和唯一键索引保证表中数据的唯一性。

* 外键约束
此外，一些存储引擎可以创建外键来保证数据完整性，外键不是索引，属于约束。
目前只有InnoDB 支持外键约束且不要求存在对应的索引，
但考虑到性能，建议在添加外键约束时建立索引。
```

* 优化数据访问
```md
索引可以让优化器在执行查询时不必检查表中所有数据，
可以显著提供查询速度，这是索引的普遍用途。

* 警告
添加索引并不总能自动改善所有类型的SQL查询性能。
有时候执行全表扫描反而更高效，这要取决于查询的行数。

实际上是使用索引通过随机IO来操作个别行的数据与有序IO操作读取所有数据的区别。
```
* 表连接
```md
在需要连接的列上使用索引可以显著提高性能，并可以再另一个表中快速找到一个匹配值。
掌握创建正确的索引来高效执行表连接的操作是关系型数据库SQL性能优化的基础。
```
* 结果排序
```md
索引把数据存储在一个有序的表格中。如果希望查询结果有序，那么就应该适当的使用索引。
通过 ORDER BY关键字可以对任意SELECT 查询的结果进行排序。

如果在需要排序的列上没有找到索引，一般会对获取的行进行内部排序。
在高并发系统中，使用预先建立的索引可以带来巨大的性能改进。
```
* 聚合操作
```md
索引可以作为一种更方便的计算聚合结果的工具。
例如在计算指定时期内所有账单的总和时，如果在日期和账户上添加合适的索引就可以更高效地执行。
```

## 关于存储引擎
```md
MySQL的存储引擎的灵活性是一把双刃剑，不同的存储引擎使用不同的机制来管理存储并获取数据。
```
* 存储引擎的功能和特性
```md
事务性和非事务性
持久性和非持久性
表和行级锁定
不同索引方法，例如 B-树，B+树，散列以及R-树
聚簇索引和非聚簇索引
主键索引和非主键索引
数据压缩
全文索引能力
```
* 存储引擎类型
```md
* MyISAM
  一种非事务性存储引擎，MySQL 5.5 之前版本默认的存储引擎。
* InnoDB
  最流行的事务性存储引擎，MySQL 5.5 版本开始默认的存储引擎。
* Memory
  基于内存的、非事务性、非持久性的存储引擎。
* 其它
  内置的 ARCHIVE、MERGE、BLACKHOLE、CSV等。
  第三方的 Federated、ExtraDB、TokuDB、NDB、Maria、InfinDB、Infobright等。
```

## 索引专业术语
* 索引技术
```md
是关于不同数据结构如何用不同的方法访问底层信息的理论。
包括 B-树，B+树，散列以及R-树。
每一种技术都采用不同的概念来实现一种特定目标或数据结构的优势。
```
* 索引实现
```md
是关于 MySQL及各种存储引擎实现不同的数据结构技术的方法。
如：MyISAM 实现B-树的方法和InnoDB就有所不同。
```
* 索引类型
```md
索引的类型包括：
主键类型、唯一键类型、辅助索引（secondary），全文本（fulltext）类型以及空间类型。
每种类型支持在单一列、多列（混合列）或者 列的一部分上定义特定的索引类型。
这些类型中的一个或多个会成为所谓的覆盖索引（covering index）。
```
