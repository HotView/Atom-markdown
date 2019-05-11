## 基本术语
用于构建C++应用程序的三个最基本的工具：编译器，链接器，归档库。
- 编译器是以C++为输入，生成目标文件。
- 归档库是以目标文件为输入，生成静态库
- 链接器是以目标文件和库为输入，生成动态库或者可执行文件。

## 命令行工具集
将上述的三种绑定到一起组成了一个工具集。
主要有7种：
- GCC
- Visual C++
- intel
- intel
- Metrowerks
- Comeau
- Borland
- Digital Mars

## IDE与构建系统
上述的编译器，链接器和归档库都是命令行工具，它们都是从外壳程序下运行的例如（bash，cmd）。当将含有几千个独立文件的大型C++项目使用命令行来构建简直是不可能的事情。

构建大型的C++应用程序有两个基本方法：
 - IDE
提供图形界面，用于组织源文件集合。
主要有四种IDE：Microsoft Visual C++，Metrowerks CodeWarrior，Borland C++Builder和Dev-C++。
 - 构建系统（make）
提供一个文本文件格式，用于描述源文件集合，以及从源文件中要生成的二进制文件。
常见的构建工具是make实用程序。

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTYyNDM1MDA1NF19
-->