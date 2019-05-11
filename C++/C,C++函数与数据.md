背景：

程序的本质就是有数据，还有处理这些数据的方法。
## C++的优越
 - 在C++中几乎不需要用到宏。用const或者enum定义明显的常量，用inline避免函数调用的开销，用template可刻画一簇函数或者类型，用namespace去避免名字冲突。
 - 不需要在你需要变量之前去声明它，以保证你能立即对他进行初始化。声明可以出现在所有的语句中，例如for 语句，也可以出现在条件语句中。
 - 不要用malloc。new运算符能将事情做的更好
 - 试着避免void*，指针算术，联合和强制，除了在某些函数或者类实现的深层之外。
 - 尽量少用和C风格的字符串。使用C++的标准库String和vector常常可以简化程序设计。



## 数据与函数的关系
函数就是用来处理数据的
数据一定是全局的，各个函数都可以处理，这样会有问题，就有了面向对象语言，将数据和处理数据的函数包装在一起，就叫做类。

数据和函数包在一起。
## C++
学习分为两个部分：
- C++语言
- C++标准库（越来越重要，好的程序员）

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5Njc4MjE1NjEsMTMxMTEzMTEyMiwxOT
Y2OTIzOTY3LDE1OTAxMTIyNDBdfQ==
-->