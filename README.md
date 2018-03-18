## 版本操作

未add前：

`git checkout -- file`可以丢弃工作区的修改

add，未commit：

`git reset HEAD file`可以把暂存区的修改撤销掉（unstage），重新放回工作区

add commit后：

HEAD指向的版本就是当前版本，因此，Git允许我们在版本的历史之间穿梭，使用命令`git reset --hard commit_id`(或者HEAD^  HEAD^^)。

穿梭前，用`git log`可以查看提交历史，以便确定要回退到哪个版本。

要重返未来，用`git reflog`查看命令历史，以便确定要回到未来的哪个版本。

## 场景:

场景1：当你改乱了工作区某个文件的内容，想直接丢弃工作区的修改时，用命令`git checkout -- file`

场景2：当你不但改乱了工作区某个文件的内容，还添加到了暂存区时，想丢弃修改，分两步，第一步用命令`git reset HEAD file`，就回到了场景1，第二步按场景1操作。

场景3：已经提交了不合适的修改到版本库时，想要撤销本次提交，参考版本回退一节，不过前提是没有推送到远程库。



本地误删文件，已提交版本库，用`git checkout HEAD file` 或者 `git reset HEAD file`还原文件

本地误删文件，未提交版本库，用`git checkout -- file`还原文件，表示用版本库里的版本替换工作区的版本



要关联一个远程库，使用命令`git remote add origin git@server-name:path/repo-name.git`

命令`git push -u origin master`第一次推送master分支的所有内容


## 分支

查看分支：git branch

创建分支：git branch <name>

切换分支：git checkout <name>

创建+切换分支：git checkout -b <name>

合并某分支到当前分支：git merge <name>

删除分支：git branch -d <name>

强行删除分支:git branch -D <name>强行删除未合并的分支


## 标签

命令`git tag <name>`用于新建一个标签，默认为HEAD，也可以指定一个commit id

`git show <tagname>`查看标签信息

`git tag -a <tagname> -m "blablabla..."`可以指定标签信息

命令`git tag`可以查看所有标签

命令`git push origin <tagname>`可以推送一个本地标签；

命令`git push origin --tags`可以推送全部未推送过的本地标签；

命令`git tag -d <tagname>`可以删除一个本地标签；

命令`git push origin :refs/tags/<tagname>`可以删除一个远程标签。
