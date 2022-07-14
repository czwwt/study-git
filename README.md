# 学习GIT

## 入门篇

### git的基本操作

1.修改文件并提交修改后推送到远端

相关命令

`vim README.md` 修改文件

`git add README.md .` 暂存修改

`git commit -m '提交信息'` 提交修改

`git remote add origin <repo>` 添加远端仓库地址

`git push origin main` 推送到远端

2.克隆仓库

相关命令

`git clone <repo>` 下载远端仓库文件到本地

3.拉取仓库的更新

相关命令

`git pull <远程主机名> <远程分支名>:<本地分支名>` 拉取远端更新到本地并合并，`git fetch` 和 `git merge FETCH_HEAD` 的简写，如果远程分支是与当前分支合并，则冒号后面的部分可以省略。

4.整合修改记录

在pull后，下一次push前，远端仓库文件被别人修改，会push失败，需要先合并。

如果别人修改的位置和我们修改的位置一样，那么就会有冲突，不能自动合并，需要手动解决冲突。

如果想直接用本地仓库强制覆盖远端，使用 `git push origin --force` 强制推送。

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

### 改写提交

`git commit --amend` 修改最近的提交信息，适用于补充漏掉的档案和修改最近提交的注解

`git revert <commitHash>` 取消指定的一次提交，适用于安全地取消过去发布的提交 

`git reset --hard <commitHash>` 遗弃提交，回退到指定的一次提交

`git reset --hard ORIG_HEAD` 取消回退，回到遗弃前

| 模式名称 | HEAD的位置 | 索引 | 工作树 |
|  ----  | ----  | ----  | ----  |
| soft | 修改 | 不修改 | 不修改 |
| mixed(默认) | 修改 | 修改 | 不修改 |
| hard | 修改 | 修改 | 修改 |

`git cherry-pick <commitHash>` 将指定的分支提交应用于当前分支

`git rebase -i <commitHash>` 合并提交，从当前合并到commitHash，commitHash不参与。或者修改提交

`git merge --squash <branchName>` 将指定分支的所有提交合并成一个提交并导入到当前分支

### 问题案例

1.刚刚提交的文件不完整，想要补充

补充完成后，使用 `git commit --amend` 进行提交。

2.想要修改刚刚的提交信息

使用 `git commit --amend`

3.提交了错误的文件，想要回退

使用 `git reset --hard HEAD～` 回退到上一个提交

4.使用reset回退了怎么还原

使用 `git reset --hard ORIG_HEAD` 还原

5.想要将前两个提交汇合到一起，变成一个提交

使用 `git rebase -i <commitHash>` 将想要汇合的提交的pick都改为s,注意这里的commitHash不包含在编辑的文件内，可以理解为这是一个坐标

6.想要修改某一个提交

使用 `git rebase -i <commitHash>` 将需要修改的提交的pick改为e，修改文件后执行 `git commit --amend` 保存修改，最后执行 `git rebase --continue` 结束修改。注意这里的commitHash不包含在编辑的文件内，可以理解为这是一个坐标

7.在当前分支修改了文件，现在想去另一个分支，但是对当前文件还不想commit

使用 `git stash`，注意，这只能暂存已经tracked的文件，即已经提交过的文件

想要暂存新的文件，使用 `git stash --include-untracked` 或者 `git stash save -u`

回到分支后，使用 `git stash list` 查看所有的暂存

使用 `git stash pop [stash]` 恢复文件，省略 [stash] 则恢复所有暂存
