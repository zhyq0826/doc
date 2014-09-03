### git push.default设置

```
  git --version
  git version 1.8.4.rc3
```


默认配置下，当使用git push命令而没有明确的指名本地分支和程参考分支的情况，会有如下提示：

```
warning: push.default is unset; its implicit value is changing in
Git 2.0 from 'matching' to 'simple'. To squelch this message
and maintain the current behavior after the default changes, use:
 
  git config --global push.default matching
 
To squelch this message and adopt the new behavior now, use:
 
  git config --global push.default simple
 
See 'git help config' and search for 'push.default' for further information.
(the 'simple' mode was introduced in Git 1.7.11. Use the similar mode
'current' instead of 'simple' if you sometimes use older versions of Git)

```

git-config(1)有单独的一节讲push.default设置:

如果git push命令没有明确指定引用规格(refspec),也就是没有指定推送的源分支和目标分支，那么git会采用push.default定义的动作。
不同的值适用于不同的工作流程模式。

push.default可用的值如下：

- nothing

不推送任何东西并有错误提示，除非明确指定分支引用规格。强制使用分支引用规格来避免可能潜在的错误。

- current

推送当前分支到接收端名字相同的分支。

- upstream

推送当前分支到上游@{upstream}。这个模式只适用于推送到与拉取数据相同的仓库，比如中央工作仓库流程模式。

- simple

在中央仓库工作流程模式下，拒绝推送到上游与本地分支名字不同的分支。也就是只有本地分支名和上游分支名字一致才可以推送，
就算是推送到不是拉取数据的远程仓库，只要名字相同也是可以的。在GIT 2.0中，simple将会是push.default的默认值。
simple只会推送本地当前分支。

- matching

送本地仓库和远程仓库所有名字相同的分支。
这是git当前版本的缺省值。 

一般来说simple够了，如果严格一点儿可以用nothing,这样来配置push.default

```
git config --global push.default simple
```
