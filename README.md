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
