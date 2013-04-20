mongodb 数组操作
***********************

数组在nosql数据库中扮演着特别的角色，某些场景下使用数组将会特别方便,例如如下场景

- 数据量较小，十万以下
- 有多对多的关系存在
- 包含正反向查询
- 不频繁更新数组中的数据

例如博客文章中的标签，可能会有一篇文章包含多个标签，一个标签对应多篇文章

-- code-block:: bash

    tag --> [
        article1,
        article2,
        article3,
        article4
    ]

    article --> [
        tag1,
        tag2,
        tag3,
        tag4,
    ]

在这种场景下，可能会需要利用标签查询特定文章，以及反向查询:查询文章包含的标签,在nosql数据库中完全可以使用数组来组织这种多对多的关系

考虑设计collection 结构，文章collection:article,标签collection:article2tag

.. code-block:: bash

    article {
        title:'',
        content:'',
        tag:[],
        atime:''
    }

    article2tag {
        tag:''
        articleList:[],
        atime:'',
        size:0
    }

article的tag键是数组类型，值为单个article的标签
article2tag的articleList键是数组类型，值为包含此标签的文章

每次文章添加新标签的时候，更新文章和标签的对应关系

.. code-block:: bash

    #!/usr/bin/env python
    #更新文章标签
    db.article.update({'_id':article_id},{'$set':{'tag':tags}})
    
    #在二者对应关系中清除之前该文章的所有关系,使用数组的$pull操作，及删除该文章和标签的所有关系,并将数组长度减小1
    db.article2tag.update({'article2list':article_id},{'$pull':{'articleList':article_id},'$inc':{'size':-1}},multi=True)
    
    #建立新的关系
    for i in tags:
        db.article2tag.update({'tag':i},{'$push':{'article2list':article_id},'$inc':{'size':1}})

    #清除不包含文章的标签
    db.article2tag.remove({'size':{'$lte':0}},multi=True)

**注意**

当数组变得很大时,$push和$pull对性能将产生比较大的影响，所以在使用$push和$pull的场景中一定是小数据量且不发生频繁更新的场景，如果你的数组会变得很大，那么考虑把数组中的数据单独提取为一个collection吧 ->:)!






