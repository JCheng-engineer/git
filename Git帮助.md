Git 基础概念（暂存区）：https://git-scm.com/book/zh/v1/%E8%B5%B7%E6%AD%A5-Git-%E5%9F%BA%E7%A1%80 

使用 SSH 连接 github
https://help.github.com/articles/connecting-to-github-with-ssh/ 

Git branch, merge, rebase, remote （链接里的整个第三章）
https://git-scm.com/book/en/v2/Git-Branching-Branches-in-a-Nutshell 

嫌教程长的可以玩互动游戏 https://learngitbranching.js.org/

Git 子模块：https://git-scm.com/book/zh/v1/Git-%E5%B7%A5%E5%85%B7-%E5%AD%90%E6%A8%A1%E5%9D%97 

GitHub flow
https://guides.github.com/introduction/flow/ 

慕夏 等学长整理的使用简介和 PPT
https://drive.google.com/open?id=1-Uj0QB0tC4bYomiMJqoXGMkXq_8esY8f

https://drive.google.com/drive/folders/1RKvHFYnOoAL-EW5FKfAIO8O2iDKevPmn






常见问题

Q: 我提的 PR github 提示和 master 有冲突，该怎么办？
A: 这里得区分是什么代码产生了冲突：
submodule 冲突了，一般来说将本地的 submodule 更新到最新的 master，然后重新在主项目 commit 和 push 就好了
项目本身代码冲突了，如果 github 网页上能够自动更新，那可以用这个。网页上的操作等同于本地 git merge, git commit, git push。如果网页上不能处理，那只能在命令行自己进行与 master 的同步。同样也是这三个步骤: git merge(rebase), git commit, git push
如何经常发现有代码冲突，说明有同样的文件总是在被不同的人修改，考虑重构代码，避免经常冲突的情况。

Q: git merge 和 git rebase 的差别？
A: https://www.jianshu.com/p/f23f72251abc 

Q: 我不小心将新代码 commit 到了本地的 master，忘记切新分支了该怎么办？
A: 首先，通过 git log 找到你新代码提交之前的 hash。然后 git reset $hash。此时你的新修改会变成未提交状态。这时切新分支，然后继续正常走 github flow 即可。

Q: git 有那些操作比较危险？
1. git pull 隐含了 merge 行为，如果不确定要做什么，慎用，而是用 git fetch 和 git merge 代替它。
2. git commit --amend 这个操作会更新当前的 commit，你将会比较难以回到 amend 之前的状态，本地开发想保持commit记录的整洁性时可以使用，其他情况下慎用。
3. git push -f 这个操作会强行更新远端的分支，你将会找不会远端分支之前的状态，慎用。并且严禁对 master 分支使用 force push