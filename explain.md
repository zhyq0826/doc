Explain

从之前的文章中，我们可以知道explain()能够提供大量与查询相关的信息。对于速度比较慢的查询来说，这是最重要的诊断工具之一。通过查看一个查询的explain()输出信息，可以知道查询使用了哪个索引，以及是如何使用的。

最常见的explain()的输出有两种类型：使用索引的查询和没有使用索引的查询。

在上一篇MongoDB的博客可以看到两种类型的explain如下：

没有使用索引时

```
{
  "cursor" : "BasicCursor",
  "isMultiKey" : false,
  "n" : 1,
  "nscannedObjects" : 1001,
  "nscanned" : 1001,
  "nscannedObjectsAllPlans" : 1001,
  "nscannedAllPlans" : 1001,
  "scanAndOrder" : false,
  "indexOnly" : false,
  "nYields" : 7,
  "nChunkSkips" : 0,
  "millis" : 1,
  "server" : "user:27017",
  "filterSet" : false
}

```

使用索引时

```

{
  "cursor" : "BtreeCursor username_1",
  "isMultiKey" : false,
  "n" : 1,
  "nscannedObjects" : 1,
  "nscanned" : 1,
  "nscannedObjectsAllPlans" : 1,
  "nscannedAllPlans" : 1,
  "scanAndOrder" : false,
  "indexOnly" : false,
  "nYields" : 0,
  "nChunkSkips" : 0,
  "millis" : 0,
  "indexBounds" : {
    "username" : [
      [
        "user1000",
        "user1000"
      ]
    ]
  },
  "server" : "user:27017",
  "filterSet" : false
}

```

我们以有索引的结果为例，来依次看一下这些字段代表的意思

```
"cursor" : "BtreeCursor username_1"
```

BtreeCursor表示本次查询使用了索引，具体来说，是使用了“username”上的索引{“username”：1}。如果查询要对结果进行逆序遍历，或者使用了多键索引，就可以在这个字段中看到“reverse”和“multi”这样的值。

```
"isMultiKey" : false
```
用于说明本次是否使用了多键索引。

```
"n" : 1
```
本次查询返回的文档数量

```
"nscannedObjects" : 1

```
这是MongoDB按照索引指针去磁盘上查找实际文档的次数。如果查询包含的查询条件不是索引的一部分，或者说要求返回不在索引内的字段，MongoDB就必须依次查找每个索引条目指向的文档。

```
"nscanned" : 1
```
如果有使用索引，那么这个数字就是查找过的索引条目数量，如果本次查询是一次全表扫描，那么这个数字就代表检查过的文档数目。

```
"scanAndOrder" : false

```
MongoDB是否在内存中对结果集进行了排序

```
"indexOnly" : false
```
MongoDB是否只使用索引就能完成此次查询。在本例中，MongoDB只使用索引就找到了全部的匹配文档，从“nscanned”和“n”相等就可以看出来。然而，本次查询要就返回匹配文档中的所有字段，而索引只包含“username”这个字段，如果就本次查询修改为

```
{"_id":0, "username":1}，

```
那么本次查询就可以被索引覆盖了，"indexOnly"的值就会是true。

```
"nYields" : 0

```
为了让写入请求能够顺利执行，本次查询暂停暂停的次数。如果有写入请求需求处理，查询会周期性的释放他们的锁，以便写入能够顺利执行。然而，在本次查询中，没有写入请求，因此查询没有暂停过。

```
"millis" : 0

```
数据库执行本次查询所耗费的毫秒数。这个数字越小，说明效率越高。

```
"indexBounds" : {...}

```
这个字段描述了索引的使用情况，给出了索引的遍历范围。由于此次查询是精确匹配，所以所以只要查“user1000”这个值就可以了。

**Hint**

虽然MongoDB查询优化器一般工作的很不错，但是也可以使用hint()来强迫MongoDB使用一个特定的索引。在这种方法下某些情形下会提升性能。一个有索引的collection并且执行一个多字段的查询。传入一个制定的索引，强迫查询使用该索引。

```
db.users.find({"username":"user1000", "age":30}).hint({"username":1})
```
注意：请确定你已经创建了相应的索引。

假设在users上有个{"a": 1, "b": 1}的索引，名称是"a_1_b_1"，则如下两种方式等价：

```
db.users.find({"a": 4, "b": 5, "c": 6}).hint({"a": 1, "b": 1})
db.users.find({"a": 4, "b": 5, "c": 6}).hint("a_1_b_1")
```
也可以强迫查询不适用索引，做表扫描：

db.users.find().hint({"$natural":1})
