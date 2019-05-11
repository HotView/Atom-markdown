就是在commit一个很大的文件，然后在工作目录删除了这个文件，并没有使用git rm
去删除，然后新的一次commit，版本库内容更换，原有删除的大文件不在现在版本库中，但是它还是存在.git文件夹下，怎么办？
[寻找并删除大文件](https://harttle.land/2016/03/22/purge-large-files-in-gitrepo.html)
## Step 1. 查看哪些历史提交过文件占用空间较大
使用以下命令可以查看占用空间最多的五个文件：
- git rev-list --objects --all
**查看所有的已经打包的文件对象**
然后将所有的文件对象传入git verify-pack 命令中，让其筛选去5个最大的文件。命令如下：
`git rev-list --objects --all | grep "$(git verify-pack -v .git/objects/pack/*.idx | sort -k 3 -n | tail -5 | awk '{print$1}')"`
	>rev-list命令用来列出Git仓库中的提交，我们用它来列出所有提交中涉及的文件名及其ID。 该命令可以指定只显示某个引用（或分支）的上下游的提交。
--objects：列出该提交涉及的所有文件ID。
--all：所有分支的提交，相当于指定了位于/refs下的所有引用。

- git verify-pack。

## step 2. （重写历史记录）
通过`filter-branch`来重写这些大文件涉及到的所有提交，删除历史提交过的大文件：

`git filter-branch --force --index-filter 'git rm -rf --cached --ignore-unmatch big-file.jar' --prune-empty --tag-name-filter cat -- --all`

上面脚本中的big-file.jar请换成你第一步查出的大文件名，或者这里直接写一个目录。

>filter-branch命令可以用来重写Git仓库中的提交
--index-filter参数用来指定一条Bash命令，然后Git会检出（checkout）所有的提交， 执行该命令，然后重新提交。
–all参数表示我们需要重写所有分支（或引用）。

在重写提交的过程中，会有以下日志输出:

`Rewrite 6cdbb293d453ced07e6a07e0aa6e580e6a5538f4 (266/266)`
 `#Ref 'refs/heads/master' was rewritten`
如果显示 xxxxx unchanged, 说明repo里没有找到该文件, 请检查路径和文件名是否正确，重复上面的脚本，把所有你想删除的文件都删掉。

## step 3. 推送修改后的repo
以强制覆盖的方式推送你的repo, 命令如下:

`git push origin master --force`

## step 4. 清理和回收空间
虽然上面我们已经删除了文件, 但是我们的repo里面仍然保留了这些objects, 等待垃圾回收(GC), 所以我们要用命令彻底清除它, 并收回空间，命令如下:
`rm -rf .git/refs/original/`
`git reflog expire --expire=now --all`
`git gc --prune=now`
至此，我们已经彻底的删除了我们不想要的文件


> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0NzYwMTQ2NDQsLTY0NTY1NTgzNiw2MT
QxODEwMjMsMzQ2MTEwMDU1LC0xMjg2OTI3NzMxLDIwODY1MzIy
NjddfQ==
-->