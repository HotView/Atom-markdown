使用命令`git add`开始跟踪一个文件。
这是个多功能命令：可以用它开始跟踪新文件，或者把已跟踪的文件放到暂存区，还能用于合并时把有冲突的文件标记为已解决状态等。
## 基本操作
 - git add \<path>
基本操作
把\<path>添加到暂存区，不仅能够判断出新添的文件，还能判断出新添的文件，并把它们的信息添加到暂存区。
- git add -u
文件对象是已经==tracked==的
把修改过的文件和已经删除文件的信息添加到暂存库
- git add -A
文件对象是已经==tracked==和没有==tracked==
已经tracked的已经被修改或被删除文件的信息添加到暂存区，还有未tracked的文件。
## 消除冲突的文件
对于一些没有merged的文件，如果使用pull操作，会报错，解决如下：
```
git add -u 
git commit
```
## 撤销add操作
详情参考：https://stackoverflow.com/a/23188613/7797869
#### S1
撤销所有文件：git reset HEAD .
撤销某个文件夹或者文件：git reset HEAD -filename
#### S2
`git rm <file>`
`git commit --amend --no-edit`
#### S3
non-interactive Rebase
```
# Create a new branch at the parent-commit of the commit that you want to remove
git branch temp <parent-commit>

# Rebase onto the parent-commit, starting from the commit-to-remove
git rebase --preserve-merges --onto temp <commit-to-remove> master

# Or use `-p` insteda of the longer `--preserve-merges`
git rebase -p --onto temp <commit-to-remove> master

# Verify your changes
git diff master@{1}
```


> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0MTY1NTQ2OTQsNjIxNjQ0MjQ5LDE0OT
E5MjgxMDEsMTI3NzQ1Mzc2Ml19
-->