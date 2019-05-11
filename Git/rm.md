与git add相似，两者的操作效果是相反的
## 概念
要从 Git 中==移除==某个文件，就必须要从已跟踪文件清单中移除（确切地说，是从暂存区域移除），==（不用再git add 了，git add是添加或者修改文件用的，与git rm 相反的操作）然后提交。== 
 
可以用 git rm 命令完成此项工作，并连带从工作目录中删除指定的文件，这样以后就不会出现在未跟踪文件清单中了。

如果只是简单的从工作目录中手工删除文件，运行git status之后就会在下方出现
`deleted: xxxx.md`
然后再运行git rm记录此次移除文件的操作：
`git rm xxxx.md`
在下一次提交之后，该文件就不再纳入版本管理了。

如果删除之前修改过并且已经放到暂存区域的话，则必须要用  强制删除选项 -f（译注：即 force 的首字母）。 这是一种安全特性，用于防止误删还没有添加到快照的数据，  这样的数据不能被 Git 恢复。
#### 保留工作区的文件
`git rm --cached \<file>`
匹配模式
`git rm log/\*.log`
注意到星号 \* 之前的反斜杠 \， 因为 Git 有它自己的文件模式扩展匹配方式，所以我们不用 shell 来帮忙展开。
此命令删除 log/ 目录下扩展名为 .log 的所有文件。 类似的比如：
`$ git rm \*~`
该命令为删除以 ~ 结尾的所有文件。
## 操作流程
- git rm ....
- git commit ....
## 附录问题
- 如果要删除一些旧提交的跟踪对象。而在工作区这些文件不存在。出现pathspec错误，则应该采取以下办法来try。用`git filter-branch`代替`git rm`;e`删除暂存区的文件。
 
`rm i`会删除文件

 
- 如果您想从历史中完全清除文件存在的所有痕迹，而其他任何解决方案都不能胜任此任务，那么这个解决方案是最好的。
- 详情查看：https://stackoverflow.com/a/23188613/7797869
1. Use the  command
`git filter-branch --force --index-filter 'git rm -r --cached --ignore-unmatch  "视觉-图像处理/图像处理、分析与机器视觉 (4th).pdf"' --prune-empty --tag-name-filter cat -- --all`
2. 完成之后，看看文件是否丢失
3.  添加`.gitignore`规则
`echo "视觉-图像处理/图像处理、分析与机器视觉 (4th).pdf" >> .gitignore`
`git add .gitignore && git commit -m "ignore rule for photos"`
4. 然后提交push
`git push -f origin master`

扩展：
`git filter-branch --index-filter 'git rm --cached --ignore-unmatch <file>'`
这将从根提交开始从所有提交中删除<file>。
如果您只想重写提交范围头~5..HEAD，然后您可以将其作为附加参数传递给filter-branch；如下:
`git filter-branch --index-filter 'git rm --cached --ignore-unmatch <file>' HEAD~5..HEAD
`
在过滤器分支完成之后，最好验证没有其他意外的更改，方法是在过滤操作之前将您的分支与之前的状态进行比较:
`git diff master@{1}`


> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2MjY3MDg3NjAsLTY5Mzg4NzU0NCwyMD
IxNTE4NjA1LDE2MTAxMzk2NjgsLTE2OTYxNzc3OTUsNTA1Mzk5
NTg5LC0xNjYwOTUzOTU0XX0=
-->