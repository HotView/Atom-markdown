git LFS与git的存储区域（仓库）不同，所以对于不同的一些文件，也就需要不同的命令指令来对不同的仓库进行处理
- 如果是对普通的仓库处理，就使用普通的git命令即可
- 如果是对Git LFS cache处理，就需要使用git lfs命令进行处理

## 安装
- windows安装了客户端的软件之后，在仓库目录文件夹下，使用命令行来安装lfs
`git lfs install `
- 追踪记录文件的类型
`git lfs track ".psd"`
## 操作
和git的基本操作效果，只是需要在git转换为git lfs。
- git lfs checkout
- git lfs pull
- git lfs push
- git lfs prune:删除
- git lfs fetch
- git lfs track


> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTM4OTUzOTgwM119
-->
