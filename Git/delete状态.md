## 查看删除的文件
`git ls-files --deleted`
## 利用管道将中文的转义字符转换为中文
`xargs echo -e `
## xargs在delete应用 
利用管道恢复多个被删除的文件，可以使用批处理命：
`git ls-files -d | xargs git checkout --`

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEyMjc0NDA1MjRdfQ==
-->