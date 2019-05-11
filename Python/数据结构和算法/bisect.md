二分模块
这个模块主要提供两个模块
- 一个是查询操作
- 一个是插入操作

## 查询操作
有返回值，返回值就是查询的元素在列表中的按照有序的顺序排类，所在的位置索引
- `bisect.bisect( list,item,left,right)`
- `bisect.bisect_left( list,item,left,right)`：如果查询的值与列表里的值相等，尽量返回靠左边的位置。
## 插入操作
将一个元素插入到列表中去，并且保持列表的有序性。
- `bisect.insort(list,item,left,right)`
- `bisect.insort_left(list,item,left,right)`：如果插入的值与列表内的元素相等，则尽量靠左边插入。

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3NjgxNDUxNDVdfQ==
-->