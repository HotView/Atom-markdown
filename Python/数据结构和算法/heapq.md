heapq是python内置的最小堆数据结构
在heapq模块里面内置而成。
最小堆的性质
This  implementation uses arrays for which 
$heap[k] <= heap[2*k+1]$
$heap[k] <= heap[2*k+2] for all k$  
counting elements from zero.
## 将一个列表转化为最小堆
heapq.heapify(list)
## 插入元素
插入元素到最小堆保持堆的性质
heapq.push(heap,item)
## 取出元素
heapq.heappop(heap)


> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTI2ODg2ODU0OF19
-->