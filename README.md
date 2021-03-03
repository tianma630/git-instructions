# Git instructions

> 原文：https://gitee.com/progit

## hash

- `git hash-object -w <file>` &emsp; 将文件转为hash存储到仓库中
- `git cat-file -p <hash>` &emsp; 获取hash内容
- `git ls-files -s` &emsp; 现实暂存区中的内容

## diff

- `git diff` &emsp; 查看修改的内容
- `git diff --staged` &emsp; 查看提交暂存区的内容

## commit

- `git commit -a -m '<comment>'` &emsp; 跳过git add，直接commit
- `git restore <file>` &emsp; 撤销修改的内容
- `git checkout -- <file>` &emsp; 撤销修改的内容(同上)
- `git restore --staged <file>` &emsp; 撤销提交到暂存区的文件
- `git reset HEAD <file>` &emsp; 撤销提交到暂存区的文件(同上)
- `git rm --cached <file>` &emsp; 撤销提交到暂存区的新增文件
- `git commit --amend -m` &emsp; 修改最后一次提交，或和当前暂存区的内容合并一起提交
- `git reset --soft HEAD~[n:1 2 3]` &emsp; 撤回最近n次的commit(撤销commit，不撤销git add)
- `git reset --mixed HEAD~[n:1 2 3]` &emsp; 撤回最近n次的commit(撤销commit，撤销git add)
- `git reset --hard HEAD~[n:1 2 3]` &emsp; 撤回最近n次的commit(撤销commit，撤销git add，还原改动的代码)
- `git show [hash]` &emsp; 查看变更详情

## log

- `git log -p -2` &emsp; 查看最近的2次commit，及修改内容
  
  - --stat  增删行数统计
- `git log --pretty=oneline` &emsp; 每次commit用1行显示
  - --pretty=[short|full|fuller]

- `git log --pretty=format:"%h - %an, %ar : %s"` &emsp; commit格式化显示
  - %H 提交对象（commit）的完整哈希字串
  - %h 提交对象的简短哈希字串
  - %T 树对象（tree）的完整哈希字串
  - %t 树对象的简短哈希字串
  - %P 父对象（parent）的完整哈希字串
  - %p 父对象的简短哈希字串
  - %an 作者（author）的名字
  - %ae 作者的电子邮件地址
  - %ad 作者修订日期（可以用 -date= 选项定制格式）
  - %ar 作者修订日期，按多久以前的方式显示
  - %cn 提交者(committer)的名字
  - %ce 提交者的电子邮件地址
  - %cd 提交日期
  - %cr 提交日期，按多久以前的方式显示
  - %s 提交说明
  
- `git log --graph` &emsp; 分支衍合情况
  - -p 按补丁格式显示每个更新之间的差异。
  - --stat 显示每次更新的文件修改统计信息。
  - --shortstat 只显示 - --stat 中最后的行数修改添加移除统计。
  - --name-only 仅在提交信息后显示已修改的文件清单。
  - --name-status 显示新增、修改、删除的文件清单。
  - --abbrev-commit 仅显示 SHA-1 的前几个字符，而非所有的 40 个字符。
  - --relative-date 使用较短的相对时间显示（比如，“2 weeks ago”）。
  - --graph 显示 ASCII 图形表示的分支合并历史。
  - --pretty 使用其他格式显示历史提交信息。可用的选项包括 oneline，short，full，fuller 和 format（后跟指定格式）。

- `git log --since=2.weeks` &emsp; 显示2周内的commit
  - --author=[author] 按作者过滤
  - --grep=[message] 按关键字过滤
  - -(n) 仅显示最近的 n 条提交
  - --since, --after 仅显示指定时间之后的提交。
  - --until, --before 仅显示指定时间之前的提交。
  - --committer 仅显示指定提交者相关的提交。 

- `git reflog` &emsp; 查看完整操作历史

## tag

- `git tag` &emsp; 显示所有标签
- `git tag -l 'v1.4.2.*'` &emsp; 显示匹配的标签
- `git tag -a v1.4 -m 'my version 1.4'` &emsp; 含附注的标签
- `git show v1.4` &emsp; 显示标签详情
- `git tag v1.4-lw` &emsp; 轻量级标签
- `git tag -d [tagName]` 删除标签
- `git push origin v1.5` &emsp; 推送标签到远程仓库
- `git push origin --tags` &emsp; 推送本地所有标签到远程仓库

## branch

- `git branch` &emsp; 查看分支
- `git checkout [branchName]` &emsp; 切换分支`
- `git branch -b [branchName]` &emsp; 创建并切换分支
- `git branch [branchName] [commitHash]` &emsp; 特定提交历史创建分支
- `git branch -v` &emsp; 查看所有分支的最后一次提交
- `git branch --merged` &emsp; 查看哪些分支已被并入当前分支
- `git branch --no-merged` &emsp; 查看哪些分支未被并入当前分支

## stash

- `git stash` &emsp; 暂存工作区和缓存区的变更
- `git stash pop` &emsp; 还原暂存的内容
- `git stash list` &emsp; 查看暂存记录
- `git stash apply [stashId]` &emsp; 取出特定的暂存的内容
- `git stash drop [stashId]` &emsp; 删除特定的暂存的内容

## rebase

- `git rebase [branchName]` &emsp; 合并主分支的更新，不生成新的commit
- `git rebase --continue` &emsp; 解决冲突后，继续rebase
- `git rebase --abort` &emsp; 取消当前的rebase
- `git rebase -i HEAD~n` &emsp; 对最近的 n 个 commit 进行 rebase 操作(合并)

## 调试

- `git blame -L 12,22 [file]` &emsp; 展示文件中第12到22行最近一次变更
- `git bisect` &emsp; 二分查找问题
  1. `git bisect start`
  1. `git bisect bad`
  1. `git bisect good v1.0`
  1. `git bisect reset`

## submodule

https://gitee.com/progit/6-Git-%E5%B7%A5%E5%85%B7.html#6.6-%E5%AD%90%E6%A8%A1%E5%9D%97

## 钩子(.git/hooks)

- pre-commit：在键入提交信息前运行, 被用来检查即将提交的快照，比如lint
- prepare-commit-msg：在提交信息编辑器显示之前，默认信息被创建之后运行
- commit-msg：用来在提交通过前验证项目状态或提交信息
- post-commit：在整个提交过程完成后运行，他不会接收任何参数，但可以运行git log -1 HEAD来获得最后的提交信息。总之，该挂钩是作为通知之类使用的。
- applypatch-msg
- pre-rebase
- post-checkout
- pre-receive
- post-receive
