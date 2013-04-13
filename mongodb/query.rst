mongodb query
********************

1.  **一般带条件find查询**
    
    mongodb 的查询使用collection 中的find方法

    .. code-block:: bash
        
        db.blog.find()

    根据条件查询并返回指定的键

    .. code-block:: bash

        db.blog.find({'tag':'sql'},{'title':1,'content':1,'atime':1})

2.  **比较查询**
    
    mongodb的查询使用$+英文缩写,比较查询包括

    ========= ===========
      操作符     含义
    ========= ===========
        $gt       大于
        $lt       小于
        $gte   大于等于
        $lte   小于等于
    ========= ===========

    查询时间大于2012-10-1 小于2013-10-1的全部文章

    .. code-block:: bash

        db.blog.find({'atime':{'$lte':new Date('2013-10-01'),'$gte':new Date('2012-10-01')})

3.  **or查询**
    
    $in 和 $or 可以查询一个键的多个值，查询标签保护多个值得文章

    .. code-block:: bash

        db.blog.find({'tag':{'in':['sql','nongodb','nosql']}})

    或者查询作者是zhyq或者标签包含这些的文章

    .. code-block:: bash

        db.blog.find({'$or':[{'tag':{'in':['sql','nosql','mongodb']}},{'author':'zhyq'}]})

4.  **null 查询**

    null 查询不仅返回tag为null的文章还返回不存在这个键的文章

    .. code-block:: bash

        db.blog.find({'tag':null})

    结果为

    .. code-block:: bash

        {'tag':null,'content':'','author':'','atime':''}
        {'content':'','author':'','atime':''}

    所以可以结合$exists查询来指定包含该键却为空的文章

    .. code-block:: bash

        db.blog.find({'tag':{'$in':[null],'$exists':true}})

5.  **exists 查询**

    $exists 可以查询文档是否包含特定的键

    .. code-block:: bash

        db.blog.find({'author':{'$exists':true}})

6.  **数组查询**

    数组查询和普通的查询没有区别,如下查询tag数组中包含sql的文章

    .. code-block:: bash

        db.blog.find({'tag':'sql'})

    如果要匹配数组中的多个元素使用$all查询,查询包含sql和nosql的所有文章，顺序无关

    .. code-block:: bash

        db.blog.find({'tag':{'$all':['sql','nosql']}})

    精确匹配整个数组，即包含特定顺序

    .. code-block:: bash

        db.blog.find({'tag':['sql','nosql','mongodb']})

    匹配数组某个位置上的元素使用list.key

    .. code-block:: bash

        db.blog.find({'tag.1':'sql'})

    $slice 操作返回数组特定长度的内容

    返回标签的前三条

    .. code-block:: bash

        db.blog.find({'tag':{'$slice':3}})

    返回标签的最后一条

    .. code-block:: bash

        db.blog.find({'tag':{'$slice':-1}})

    跨过前10条，返回10条之后的10条

    .. code-block:: bash

        db.blog.find({'tag':{'$slice':[10,10]}})

7.  **数组查询的陷阱**

    假如有如下数据

    .. code-block:: bash

        {'tag':5,'content':'','atime':'','author':''}
        {'tag':[0,5],'content':'','atime':'','author':''}
        {'tag':[5,10],'content':'','atime':'','author':''}
        {'tag':[10,20],'content':'','atime':'','author':''}

    现查询tag中所有元素 >-1 and <11

    .. code-block:: bash

        db.blog.find({'tag':{'$gte':-1,'$lte':11}})

    结果 {'tag':[10,20],'content':'','atime':'','author':''} 也被查询出来了，因为在mongodb内部对于数组的范围查询不管其是否是同一个元素满足条件，对于这条数据
    因为10<11，20>-1，所以满足条件,如果要想让数组中的满足条件的元素是同一个元素使用$elemMatch

    .. code-block:: bash

        db.blog.find({'tag':{'$elemMatch':{'$gte':-1,'$lte':11}}})

    此时 {'tag':5,'content':'','atime':'','author':''}这条数据又没有了，因为$elemMatch只对数组起作用，如果不是数组的数据直接排除了，如果查询的结果既需要数组又需要不是数组呢?使用min和max方法

    .. code-block:: bash

        db.blog.find({'tag':{'$gte':-1,'$lte':11}}).min({'tag':-1}).max({'tag':11})

8.  **not 查询**

    即对查询的结果取反

    .. code-block:: bash

        db.blog.find({'tag':{'$not':{'$mod':[5,1]}}})




