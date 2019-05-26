```c
void Unweighted(Vertex s)
{
	Enqueue(s,Q);
	while(Q)
	{
		V = Dequeu(Q)
		for(V 的每一个邻接点w)
			if （dist[w]==-1）
			{
				dist[w] =dist[V]+1;
				path[w] = V;
				Enqueue(w,Q);
			}	
	}
}
```

## 特点
- 需要判重，BFS判重的方法可以用bool数组，然后true表示走过节点，false表示没走过的节点，如果是比较复杂的状态等，则可能需要hash了（当《算法导论》中DFS跟BFS用的都是OPEN跟CLOSE表）
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbNTI4MTQ1NzEzXX0=
-->