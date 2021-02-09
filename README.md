# Git instructions

## diff

- `git diff` &emsp; 查看修改的内容
- `git diff --staged` &emsp; 查看提交暂存区的内容

## commit & restore

- `git commit -a -m '<comment>'` &emsp; 跳过git add，直接commit
- `git restore <file>` &emsp; 撤销修改的内容
- `git checkout -- <file>` &emsp; 撤销修改的内容(同上)
- `git restore --staged <file>` &emsp; 撤销提交到暂存区的文件
- `git reset HEAD <file>` &emsp; 撤销提交到暂存区的文件(同上)
- `git commit --amend` &emsp; 修改最后一次提交，或和当前暂存区的内容合并一起提交

### log

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

## tag

- `git tag` &emsp; 显示所有标签
- `git tag -l 'v1.4.2.*'` &emsp; 显示匹配的标签
- `git tag -a v1.4 -m 'my version 1.4'` &emsp; 含附注的标签
- `git show v1.4` &emsp; 显示标签详情
- `git tag v1.4-lw` &emsp; 轻量级标签
- `git push origin v1.5` &emsp; 推送标签到远程仓库
- `git push origin --tags` &emsp; 推送本地所有标签到远程仓库
