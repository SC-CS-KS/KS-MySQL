# 索引页
```md
InnoDB 是索引组织表，因此聚集索引页的叶子节点中存放着完整的记录，
辅助索引页中记录存放着指向叶子节点的书签。

B+ 树索引定位到记录所在的页，再通过二叉查找算法进行进一步的比较。
```

## 页
```md
页是InnoDB存储引擎的最小存储单位，通过UNIV_PAGE_SIZE来定义。

* 物理页指存储在外部存储设备上，习惯上用 Block 表示。
* 逻辑页存储在缓冲池中，习惯上用 page 描述。

* 索引页（index page）
  在InnoDB 中实际是数据页，存放实际的数据。

* undo 日志页
  用来存放 undo 日志，主要用来完成事务的回滚操作。
  由于 undo 日志包含了记录的更新项，可以用来构造当前记录的前一个版本，
  因此还用来做多版本控制。

## 存储结构
#### Page Header
```md
用来保存页的信息，占56字节，位于File Header 之后。
```

## Page Cursor

