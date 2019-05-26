
**深度优先搜索的步骤分为 1.递归下去 2.回溯上来。顾名思义，深度优先，则是以深度为准则，先一条路走到底，直到达到目标。这里称之为递归下去。因其每次会返回的特点DFS在枚举算法里也称为回溯法，DFS走的路径被称为解答树。**
## 基本思想
由图可知，我们可以走上下左右四个方向，我们规定按照左下右上的方向顺序走，即，如果左边可以走，我们先走左边。然后递归下去，没达到终点，我们再回溯上来，等又回溯到这个位置时，左边已经走过了，那么我们就走下边，按照这样的顺序与方向走。==并且我们把走过的路标记一下代表走过，不能再走（不能再入栈，重复操作了）==。
```c
void DFS(int graph[][],int used[][],int x,int y)
{
	if (graphy[x][y] == graph[goal_x][goal_y])
	{
		printf("successful");
		flag = 1;
		return ;
	}
	for (int i = 0;i<4;i++)
	{
		if(used[x+dx[i]][y+dy[i]] == 0 && !flag)
		{
			used[x+dx[i]][y+dy[i]] = 1;//设置为走过
			DFS(graph,used,x+da[i],y+dy[i]);
			used[x+dx[i]][y+dy[i]] = 0;//状态回溯，退回来，将格子设置为未走过
		}
	}
}	

```
## 特点
- 比广度慢，但是空间小。
- DFS以解答树遍历，不会重复，无需判重，但如果是用DFS进行回溯法枚举，则可能需要判重
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTgxNzA1NTg5OF19
-->