单个的c++文件我们可以用g++来编译；
但是当我们有很多的cpp文件时，我们如果手动一个一个编译则不是一个好的办法，而Cmake就是针对这种状况应运而生的。

使用CMake来进行Compiling，Linking，Install software for Unix！
## 跨平台的CMake
CMake是用来产生不同平台下构建文件的软件，它通过CMakeLists.txt文件来进行生成不同平台下的==将要构建的文件！==

以下是不同平台的构建文件，用来构建最终生成的程序！
系统平台|build files
---|---
Unix|使用CMake通过CMakeLists.txt文件生成Makefile，在Unix下使用Makefile来构建生成的文件
Mac OS X|使用XCode来构建文件
Windows|使用Visual Studio来构建文件
## 总体的步骤
- 创建一个项目文件夹
- 将源文件移动到项目文件夹中
- 在项目文件夹中新建一个CMakeLists.txt
- 编写CMakeLists.txt文件
- 返回项目文件夹下执行`$ cmake .`命令

## CMake一些变量参数配置
可选变量|说明
--|--
CMAKE_INSTALL_PREFIX=/a/path|安装路径
BUILD_SHARED_LIBS|构建共享库
CMAKE_BUILD_TYPE= Debug|产生调试标志设置的文件
CMAKE_C_COMPILER=icc|设置编译器为icc
CMAKE_CXX_FLAGS= "-O3"|设置编译器的优化级别为3
CMAKE-PREFIX_PATH = /a/path|搜索依赖项

`cmake -CMAKE_INSTALL_PREFIX=/a/path \ -CMAKE_BUILD_TYPE= Release... \  /path/to/src`
==最后一个路径是CMakeLists.txt所在的根目录！==
## CMakeLists.txt
```python
cmake_minimum_required(VERSION 3.10)
set(CAMKE_BUILD_TYPE Debug)
set(CMAKE_CXX_FLAGS "${CMAKE_CXX_FLAGS} -std=c++14

project(sample)

add_executable
(
sample//输出文件路径名字
main.cpp//要编译的源文件
)

```

## Unix下的Makefile配置
- 项目文件夹下执行`$ make`命令，编译源代码，生成目标文件。它从Makefile中读取指令，然后编译。
- 项目文件夹下`$ make install`，执行安装标签（目标），也就是把文件复制到某些目录。它也从Makefile中读取指令，安装到指定的位置（一般需要root权限！）。
![make file 示例](https://github.com/HotView/Images/raw/master/TIM%E6%88%AA%E5%9B%BE20190214190137.png)
Makefile的写法
名字：makefile或者Makefile
```
target：dependencies
			command
结果：需要的输入或者依赖
	执行的命令
clean:
	rm *.o main 
//删除所有的.o文件和main的文件。
```
一般分别将 .c文件编译成 .o文件，这样当某一个变动时，其他的就不用变动。

- 清除文件
`make clean`:表示要运行makefile中clean的那一段代码。
- 设置变量
CC=gcc
makefile代码中的$(CC)就代表gcc！
CFLAGS= -lm -Wall -g
$(CFLAGS)就可以使用！
 - 编译多个可执行文件
makefile只根据第一条来进行，然后根据第一条的依赖继续执行下面的。其他的就会别跳过。
解决办法：
加一个all
`all : main_min main_max`




## Windows下的visual studio的配置

- 创建一个项目文件夹
- 将源文件移动到项目文件夹中
- 在项目文件夹中新建一个CMakeLists.txt
- 编写CMakeLists.txt文件
- 打开CMake软件，将上述的项目文件夹的路径填入source code一栏，将生成的需要build的文件路径放置在build the binaries一栏。用软件分别进行==configure==和==generate==操作
- 进入build the binaries里的路径，用visual studio打开后缀为.sln的文件
- 在visual studio中直接build即可！
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3MjIyODE0MjgsNTU5MzMwMzExLDU0Nz
I5Mzg4NywtMTUyNDE0NDI4OCwyMDQ5NTMxNzU5LDE0MjYwNjA3
MiwtMTY3ODMxNTAyOSwtMTU3MTI1NjM1MSwtNjQ4MTk1MTY2LC
0xODYwNjE2MDM0LC02MDUzMzMxNTIsOTk4MDc2Mjk2LC03MjQ2
NDY1NDhdfQ==
-->