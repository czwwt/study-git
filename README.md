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
