# 学习GIT

## 高级篇

### 分支

1.创建分支

相关命令

`git init` 初始化git 

`git branch <branchName>` 创建分支

`git switch <branchName>` `git checkout <branchName>` 切换分支

`git checkout -b <branchName>` 创建并切换分支

2.合并分支

相关命令

`git merge <branch>` 将指定分支合并到当前分支

`git branch -d <branch>` 删除分支 

`git log --graph --oneline` 查看提交日志

3.并行操作

将本地新的内容和远端新的内容在不同分支进行管理

4.用rebase合并

使用rebase可以使提交的历史记录显得更简洁。

相关命令

`git rebase <branch>` 将当前分支合并到指定分支

`git reabse --continue [msg]` rebase的时候，修改冲突后的提交不是使用commit命令，而是执行rebase命令指定 --continue选项。若要取消rebase，指定 --abort选项。

### 标签

相关命令

`git tag <tagName>` 添加轻标签

`git tag -a <tagName>` `git tag -am <msg> <tagName>` 若要添加注解标签，可以在tag命令指定 -a选项执行。执行后会启动编辑区，请输入注解，也可以指定-m选项来添加注解。

`git tag -d <tagName>` 删除标签

`git tag` 查看标签

`git tag -n` 查看标签和注解