# Storage Engine


![](../pic/MySQL-Storage-Engines.png)

* ARCHIVE	用与数据存档（行被插入后不能再修改）
* BLACKHOLE	丢弃写操作，读操作会返回空内容
* CSV	在存储数据时，以逗号分隔各个数据项
* FEDERATED	用来访问远程表
* InnoDB	具备外键支持的事务存储引擎
* MEMORY	置于内存的表
* MERGE	用来管理多个MyISAM表构成的表集合
* MyISAM	主要的非事务处理存储引擎
* NDB	MySQL集群专用存储引擎
