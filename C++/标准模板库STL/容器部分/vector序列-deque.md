向量是最简单的STL容器，其数据机构与数组类似，占据着一个连续的内存块。
当将一个元素插入到已满的向量中时，会为向量分配一个更大的内存块，将向量中的元素复制到新的内存块中，然后释放旧的内存块。
## 成员函数
 - pop_back：删除向量的最后一个元素。
 - push_back：在向量末尾插入元素。
 - begin：返回一个迭代器，该迭代器引用向量的第一个元素。
 - end：返回一个迭代器，该迭代器位于向量的最后一个元素之后。
 - size：返回向量中元素的个数。
## 增强版Deque
它向向量一样，可以快速的随机访问任意一个元素，并且能够高效的插入和删除容器的尾部元素。但是它又与vector不同，deque支持高效的插入和删除容器头部的元素，因此也叫做双端队列。
- push_front
- push_back
- pop_front
- pop_back

## 两者的迭代器
- vector，deque 的迭代器都是是一个Random Access Iterator。
- 支持算术运算，所以也支持索引操作。
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTMzMzA1OTUwMF19
-->
