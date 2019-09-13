## BFS：
首先以一个未被访问过的顶点作为起始顶点，比如以1号顶点作为起点，将1号顶点放入队列，然后将与1号顶点相邻未被访问过的放入队列中，直到所有的顶点都被访问过。
 - 空间是指数级别的
 - 不会有爆栈的风险
 - 最短，最小

## DFS：
首先以一个未被访问过的顶点作为起始顶点，沿着当前顶点走到未访问的顶点；当没有未访问过的顶点时，则回到上一个顶点，继续试探访问别的顶点，直到所有的顶点都被访问。
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
