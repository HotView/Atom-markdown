背景：
	在C++中，名称（name）可以是符号常量，变量，宏，函数，结构，枚举，类和对象等等。为了避免，在大规模程序的设计中，以及在程序员使用各种各样的C++库时，这些标识符的命名发生冲突，标准C++引入关键字namespace，可以更好地控制标识符的作用域。
==解决多模块的符号冲突问题，使用名称空间。==
## 定义命名空间：
有名的
```c++
namespace name{
			声明序列
}
```
无名的
```
namespace {

}
```
可以在命名空间的定义内，定义命名空间的成员（==内部定义==）。也可以只在命名空间的定义内声明成员，而在命名空间的定义之外，定义命名空间的成员（==外部定义==）。

## 作用域解析运算符（::）
对命令空间成员的引用，需要使用命名空间的作用域解析运算符::。

## using指令
为了省去每次调用std成员，都要添加std的麻烦，可以使用标准C++的using编译指令来简化对命名空间的名称的使用。
## using声明
`using 命名空间名::[命名空间名::.....]成员名`
注意关键字后面并没有跟关键字namespace，而且最后必须为命名空间的成员名。

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE4NTI3MTM4NjNdfQ==
-->