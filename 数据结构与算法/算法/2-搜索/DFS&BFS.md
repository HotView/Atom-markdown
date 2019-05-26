BFS：
 - 空间是指数级别的
 - 不会有爆栈的风险
 - 最短，最小

DFS：
- 空间和深度成正比
- 有爆栈的风险，比如树的深度可能有10000层
- 不能搜最短，最小

==DFS比较容易写==

## 最小的深度
```py
def minDepth(root):
	if (!root) return 0
	int left  = minDepth(root->left)
	int right  = minDepth(root->left)
	if !left|| !right return left+right+1
	return min(left,right)+1
```
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3MzIzOTg2OTZdfQ==
-->