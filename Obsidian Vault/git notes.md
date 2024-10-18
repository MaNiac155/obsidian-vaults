`git init` 创建版本库

`git add <file>` 添加到仓库

工作区 -> stage（暂存区）

`git commit -m "memory comments"` 提交到仓库 `-a` 不添加注释

stage -> main分支

`git status` 查看仓库当前状态

`git diff <file>` 查看某文件的difference

`git log` 查看版本记录 提交历史

`--pretty=oneline` 单行显示

`git reset --hard commit_id` 回退到版本号为`commit_id`的版本。

当前版本`HEAD` 上一版本`HEAD^` 上上版本`HEAD^^` 很多版本前`HEAD~20`

去未来版本用版本号

`git reflog` 查看命令历史，确定要传送的版本号

`git restore <file>` 对于修改后，没有添加到暂存区的文件，丢弃工作区的修改内容

`git restore --staged <file>` 对于已添加到暂存区的文件，撤销add，回到暂存区

`git rm <file>` 在仓库中删除，作为修改添加到暂存区，后面需要`git commit`

先创建repo`learngit.git`

`git remote add origin git@github.com:MaNiac155/learngit.git` 关联远程库

`git push -u origin master` 推送master分支

`git push origin master` 推送最新修改