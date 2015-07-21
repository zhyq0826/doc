git 使用技巧
**************************

1. **过滤不需要提交的文件**

   在 .git/info 目录下面有一个exclude文件，使用vi把这个文件打开，添加上需要过滤的文件如下,每次提交时这些文件会被过滤，这个配置对此项目全局有效
   
   .. code-block:: bash
        
       # git ls-files --others --exclude-from=.git/info/exclude
       # Lines that start with '#' are comments.
       # For a project mostly in C, the following would be a good set of
       # exclude patterns (uncomment them if you want to use them):
       # *.[oa]
       # *~
       *.pyc
       *.swp
       *.rst~
       * doc/
       

2. **git 报401错误 且不提示用户名和密码的解决办法**
   
   .. code-block:: bash
       
       $ git clone http://github.com/zhyq0826/git-doc
       error: The requested URL returned error: 401 while accessing https://github.com/zhyq0826/git-doc.git/info/refs
       fatal: HTTP request failed
   
   - 在$HOME下创建 _netrc文件，在其中写入如下内容
   
     .. code-block:: bash
        
         machine http://github.com
         login your_username
         password your_password
     
   - 在执行命令式直接提供username和password，如下
     
     .. code-block:: bash
     
          $ git clone http://username:password@github.com/zhyq0826/git-doc

3. **使用 git stash 命令临时保存本地修改**

   进行部署时经常需要修改本地配置文件如dbconf文件，conf文件，但这些文件在代码更新时不需要更新和变动可以是用git stash 命令临时保存这些修改
   
   .. code-block:: bash
   
        $ git stash 
        
   等代码更新之后再还原之前的更改
   
   .. code-block:: bash
   
        $ git stash apply
        
4. **git push -u origin master**

   .. code-block:: bash

         Branch master set up to track remote branch master from origin.

   在本地建立一个项目之后需要推送到远端的服务器，如果是第一次推送到远端，本地git并不知道把它推送到远端的什么分支，如果你推送的分支是需要经常推送到这个分支的，那么则指定 -u 参数
   以后每次push 或 pull的时候就不需要在指定分支
   
   参见 `what-exactly-does-the-u-do-git-push-u-origin-master-vs-git-push-origin-ma <http://stackoverflow.com/questions/5697750/what-exactly-does-the-u-do-git-push-u-origin-master-vs-git-push-origin-ma>`_


5. **强制撤销远程分支的某次修改**

   当不小心把某次不需要的提交推送到远程分支后，可以使用 git reset --hard commitid 和 git push origin +branch:branch  强制覆盖远程分支

    
   在本地撤销提交

   .. code-block:: bash
   
        $ git reset --hard cfa2fa929820f94831d905615ede57688a0912e6

   强制推送到远程分支

   .. code-block:: bash
   
        $ git push origin +stable:stable 


6. **删除远程标签**  

```

git tag -d tag
git push origin :refs/tags/tag

```
