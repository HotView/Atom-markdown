这些类型具有数据结构中顺序表和链表的双重优点
- 直接索引（顺序表）
- 动态分配（链表）
- 内存占用较大
- 指针访问元素，额外的存储开销
## 字符串
## 列表
python中的列表的功能（相对于C++），可以存储不同类型的数据。
- vector（相对来说效率很高）
- list（性能有局限）
- stack（基本能满足）
## 元组
不可变化版的list对象类型，也可以存储不同的对象类型。
## ndarray
- Python中内置类型数组不支持多维数组
- 列表类型，开销太大，每个元素都有指针索引，元素类型可以不相同

鉴于上述两条，所以为了加快矩阵（多维数组）的运算，就新建了ndarray类型，在numpy库中可以使用。
## collections的queue



> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbNDUwMjgxNDEzLDkzMTc3NDUxMiwxNjc1Mj
Y2OTg1XX0=
-->