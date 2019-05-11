==对于未跟踪的文件夹和文件以下的两个操作不会有影响==
### 用法
- 只改变缓存区
`git reset <file>`
从缓存区移除特定文件，但不改变工作目录。它会取消这个文件的缓存，而不覆盖任何更改。
`git reset`
重设缓冲区，匹配最近的一次提交，但工作目录不变。它会取消  _所有_  文件的缓存，而不会覆盖任何修改，给你了一个重设缓存快照的机会。
- 改变缓存区和工作区
`git reset --hard`
重设缓冲区和工作目录，匹配最近的一次提交。除了取消缓存之外，==`--hard` 标记告诉 Git 还要重写所有工作目录中的更改==。换句话说：它清除了所有未提交的更改，所以在使用前确定你想扔掉你所有本地的开发。

	`git reset <commit>`
将当前分支的末端移到  `<commit>`，将缓存区重设到这个提交，但不改变工作目录。所有  `<commit>`之后的更改会保留在工作目录中，这允许你用更干净、原子性的快照重新提交项目历史。

- 修改工作区和暂存区
`git reset --hard <commit>`
将当前分支的末端移到  `<commit>`，将缓存区和工作目录都重设到这个提交。它不仅清除了未提交的更改，同时还清除了  `<commit>`  之后的所有提交。
## git checkout 
`git checkout` 命令用于从历史提交（或者 stage 缓存）中拷贝文件到工作目录，也可用于切换分支。
#### 变换的主体是工作区和暂存区
```
git checkout .
git checkout -- [file]
```
当执行  `git checkout .`  或者  `git checkout -- [file]`  命令时，会用==暂存区==全部或指定的文件替换==工作区==的文件。这个操作很危险，会清除工作区中未添加到暂存区的改动。

#### 变换的主体是（版本库）与（暂存区，工作区）
```
git checkout HEAD .
git checkout HEAD [file]
```
当执行 `git checkout HEAD .` 或者 `git checkout HEAD [file]` 命令时，会用 `HEAD` 指向的 `master` 分支中的全部或者部分文件替换暂存区和以及工作区中的文件。这个命令也是极具危险性的，因为不但会清除工作区中未提交的改动，也会清除暂存区中未提交的改动。


> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMzg0MzE1MDEsMTU3MTc4Mzc2MywtMTc1ND
U5NzU3LDEyNjMzNzI1MDcsNTA0OTg5OTIxLDEwOTc2NTgyNjQs
MjEwODU2Mjc4OSwxMzgwOTM1OTk5LDE0MjQ5NDY1NzIsLTIwNj
YwNTEwNTNdfQ==
-->