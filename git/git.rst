
git 版本控制利器
*************************

git 介绍
======================

git 是一个快速、可扩展的分布式版本控制系统

git 安装与配置
=======================

在ubuntu下安装如此简单

.. code-block:: bash

   $ sudo apt-get install git 

迁出github上的项目
=====================

我们的所有代码都存放在github上，开发已有项目首先需要迁出线上的代码，这一
步叫克隆项目。在此以git-doc为例，迁出线上项目。

.. code-block:: bash
    
    $ git clone https://github.com/zhyq0826/git-doc.git

此命令执行之后将在本地文件夹下面创建一个git-doc目录，其中就是我们迁出的项目git-doc


使用git进行代码管理
=====================

现在git-doc中创建或修改了一个文件比如修改了main.py文件，创建了一个test.py
现在可以使用如下命令：

.. code-block:: bash

    $ git status

查看哪些文件是被我们修改的，哪些是我们创建,执行命令之后，文件的状态如下：

.. code-block:: bash

    # On branch master
    # Changes not staged for commit:
    #   (use "git add <file>..." to update what will be committed)
    #   (use "git checkout -- <file>..." to discard changes in working directory)
    #    
    #   modified  main.py 

    # Untracked files:
    #   (use "git add <file>..." to include in what will be committed)
    #
    #  test.py 

现在把修改的文件提交的版本库中，执行命令：

.. code-block:: bash

    $ git add main.py  test.py 

add 命令是把我们修改的文件添加到版本控制系统中，但是还未提交,状态如下：

.. code-block:: bash

    # On branch master
    # Changes to be committed:
    #   (use "git reset HEAD <file>..." to unstage)
    #
    #	modified:   main.py
    #   newfile     test.py

文件添加之后就可以提交到版本库中了，使用commit命令进行提交：

.. code-block:: bash

    $ git commit -m"修改了main.py和test.py文件"
    
每次提交把我们修改的东西写在m参数中来标志此次做了什么修改，status，add，commit 命令是使用git 最基本的三个命令

.. code-block:: bash

    $ git status  
    $ git add  filename
    $ git commit -m""


撤销文件的更改
===================


撤销add命令的更改
-----------------

使用add命令把文件添加到版本库中之后，如果我们想撤销此次的添加，但是保留对文件的修改，可以使用reset 命令 

.. code-block:: bash

    $ git reset main.py 
    Unstaged changes after reset:
    M   main.py
    

如果想撤销此次添加，并且撤销对文件的修改，可以使用git checkout 命令

.. code-block:: bash

    $ git checkout main.py
    
    
撤销commit命令的更改
--------------------

使用commit命令把文件提交到版本库之后，我们可以使用git reset HEAD 命令来撤销此次的提交，这时需要知道之前提交状态的id，
git 保留和记录了我们所有commit动作的id和日期，以及作者，可以使用git log 命令查看

.. code-block:: bash

    $ git log 
    
    commit 13332ef0c9dc18f79afa945f482dc8d742fbe2f7
    Author: zhyq0826 <zhyq0826@gmail.com>
    Date:   Tue Oct 30 12:46:11 2012 +0800

        删除原有合作方banner图片

    commit 6e4999bdae60db3b253492830bc27856f1d90423
    Author: zhyq0826 <zhyq0826@gmail.com>
    Date:   Mon Oct 29 18:41:13 2012 +0800

        调整裁图色调

    commit 136581a5cc9db37969afe678daf173e5dfc46819
    Author: zhyq0826 <zhyq0826@gmail.com>
    Date:   Fri Oct 26 19:41:43 2012 +0800


如果想回退到最新一次的提交状态，可以:

.. code-block:: bash

    $ git checkout  13332ef0c9dc18f79afa945f482dc8d742fbe2f7
    
执行命令之后，所有修改的文件将回到Tue Oct 30 12:46:11 2012的提交状态


git 分支开发
====================

每个项目在建立之初都有一个主分支称为master，master里的代码是经过严格测试的且一般无重大bug的分支，所以开发人员在开发新功能时为了避免影响已有的代码，需要建立自己的分支来进行开发调试，直到代码稳定之后再合并到主分支中，这一步叫merge

在新建分支之前，首先使用git branch 命令查看已有项目的分支状况

.. code-block:: bash
    
    $ git branch
    * master
    
可以看到在git-doc的项目下只有一个分支，即主分支master，查看分支状态

.. code-block:: bash

    $ git branch -r 
    origin/HEAD -> origin/master
    origin/master

现在开始新建，分支，新建分支还是使用 git branch 命令，后面跟分支名

.. code-block:: bash

    $ git branch dev

新建之后，查看分支状态

.. code-block:: bash

    $ git branch 
      dev
    * master

可以看到已经建立了分支dev，* 表示当前所在的分支，这个新建的分支还在本地，并未推送到远端服务器。

现在切换刚才新建的分支dev，使用git checkout 命令

.. code-block:: bash

    $ git checkout dev
    Switched to branch 'dev'

查看当前所在分支

.. code-block:: bash 

    $ git branch
    * dev
      master

星号已经在dev前面了，表示已经切换到了dev这个分支下面。现在这个分支下面进行开发，使用之前提到的git add  git commit 命令来提交修改的代码，然后把本地分支使用git push 命令推送到服务器，在线上建立自己的分支

.. code-block:: bash

    $ git add xxx.py
    $ git commit -m"修改了xxx.py"
    $ git push origin dev

到此本地分支就推送到线上了。

git push 命令在推送非master分支时必须指定分支名称，且必须加上origin参数，如果是推送master分支，直接使用git push 就可以。



更新本地代码
================

如果线上的分支代码被别人修改过，在本地push时会被服务器拒绝，提醒你需要更新代码，才能push，这时候就需要使用与push动作刚好相反的命令pull来更新本地代码

.. code-block:: bash

    $ git pull 
    
与git push 一样，git pull 是更新master的代码,如果更新分支代码，也需要使用origin 参数

.. code-block:: bash

    $ git pull origin dev 


删除本地分支
=================    

当不再需要本地分支的时候，可以很轻松的删除本地分支

.. code-block:: bash

    $ git branch -D dev

命令执行之后，本地分支将被删除



删除远端分支
=====================

当不再需要远端的分支的时候，可以考虑将其删除

.. code-block:: bash

    $ git push origin  :dev
    - [deleted]         dev

命令执行后远端分支将被删除










