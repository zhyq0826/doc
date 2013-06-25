git branch 命令
*******************

1. **git branch**               

   列出本地已经存在的分支

2. **git branch -r**
    
   列出远程分支

3. **git branch -a**

   列出本地和远程分支

4. **git branch branchname**

   新建分支
   
5. **git branch -m | -M oldBranch newBranch**

   重命名分支，如果newbranch名字分支已经存在，则需要使用-M强制重命名，否则，使用-m进行重命名。
    
6. **git branch -d | -D branchname**

   删除本地branchname分支

7. **git branch -d -r branchname**

   删除远程branchname分支
   
8. **git help branch**

   查看branch命令的帮助
   
9. **git checkout -b branchname**
    
   新建分支并且切换

10. **git fetch origin androidesk-1.0**
   
    clone 远程分支
