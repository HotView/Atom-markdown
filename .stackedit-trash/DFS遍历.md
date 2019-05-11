

## 实现的方式
- 可以使用递归来实现。
- 可以使用栈来实现。

## 算法（边出栈边入栈）
循环
- 先出栈
- 遍历第一个相邻的所有结点
- 判断是否是要寻找的那个？
- 是的return ； 否则入栈
## python
栈的实现
根节点先入栈
1. 出栈
2. 判断是否有误临界点
3. 如果有将出栈的那一点的子节点入栈
4. 没有的出栈
5. 重复2
```python
graph = {
	"a":["b","c"],
	"b":["a","c","d"],
	"c":["a","c","d","e"],
	"d":["b","c","e","f"],
	"e":["c","d"],
	"f":["d"]
	
}
## pop默认取出最后一个元素，符合栈的规则
def DFS(graph,s):
	stack = []
	stack.append(s)
	seen = set()
	seen.add(s)
	while(len(stack)>0):
		vertex = stack.pop()#先出栈。
		nodes = graph[vertex]#取出相邻的一层；
		for w in nodes:
			if w not in seen:#判断是否被访问过。
				stack.append(w)#没有的话就入栈。
				seen.add(w)#访问状态标记为被访问过。
		print(vertex)
```


## C++实现
```C
std::stack unvisited;

unvisited.push(&nodes[0]);

while(!univisited.empty())
{
	current = (unvisited.top());
	unvisited.pop();
	if (current->right != NULL)
		unvisited.push(current->right);
	if (current->left != NULL)
		unvisited.push(current->left);
	cout<<current->self<<endl;
}

```

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTYyNzgzNzA3OF19
-->