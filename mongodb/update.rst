mongodb的更新操作
==========================

.. code-block:: bash

    db.blog.update({},{'$set':{'tag':tag}})

    #remove key togethor
    db.blog.update({},{'$unset':{'tag':1}})

    db.blog.update({},{'$set':{'comments.0.votes':1}})

    #change all comments'author that author = tom to Jim 
    db.blog.update({'comments.author':'Tom'},{'$set':{'comments.$.author':'Jim'}})

    #remove the tag fisrt elem
    db.blog.update({},{'$pop':{'tag':1})

    #remove the tag last elem
    db.blog.update({},{'$pop':{'tag':-1}})

    #remove all elem witch is 1
    db.blog.update({},{'$pull':{'tag':1}})

    #update array
    db.blog.update({},{'$push':{'tag':'1'}})

    #update array makr sure value is unique
    db.blog.update({},{'$addToSet':{'tag':'1'})

