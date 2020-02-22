# 索引

* [数据库索引](https://github.com/SunnnyChan/knowledge-Sys-of-DB/blob/master/db-system/index/README.md)

## 聚集索引
```md
在 InnoDB 中，表数据文件本身就是按B+Tree组织的一个索引结构，这棵树的叶节点data域保存了完整的数据记录。
这个索引的key是数据表的主键，因此 InnoDB 表数据文件本身就是主索引。
```
```md
因为InnoDB的数据文件本身要按主键聚集，所以InnoDB要求表必须有主键（MyISAM可以没有），
如果没有显式指定，则MySQL系统会自动选择一个可以唯一标识数据记录的列作为主键，
如果不存在这种列，则MySQL自动为InnoDB表生成一个隐含字段作为主键，这个字段长度为6个字节，类型为长整形。
```

## 辅助索引
```md
InnoDB的辅助索引 data 域存储相应记录主键的值而不是地址。
辅助索引搜索需要检索两遍索引：首先检索辅助索引获得主键，然后用主键到主索引中检索获得记录。
```

## Q&A
* 为什么不建议使用过长的字段作为主键?
```md
因为所有辅助索引都引用主索引，过长的主索引会令辅助索引变得过大。
```
* 为什么推荐适用自增主键作为索引？
```md
因为 InnoDB 数据文件本身是一颗B+Tree，非单调的主键会造成在插入新记录时数据文件为了维持B+Tree的特性而频繁的分裂调整，十分低效。
```

## Reference
* [创建高性能索引](https://github.com/SunnnyChan/sc.ebooks/blob/master/db/hp-mysql/chapter/chapter-5-1_index.md)
