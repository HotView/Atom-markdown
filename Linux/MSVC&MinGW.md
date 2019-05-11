前言：
==两者都是用于编译链接生成Windows程序的工具，只是实现不同==
- MSVC是Windows原生的编译链接器；
- MinGW是将Linux的GUN移植到Windows下的链接编译器。
## MinGW
**MinGW**（**Min**imalist  **G**NU for  **W**indows）
通过在Windows下模拟Linux下的命令来进行编译链接生成可执行程序的过程。
- 安装MinGW，之后设置环境变量，使得其path指向安装的MinGW下的bin目录。
- 然后在文本编辑器下，编写好源代码程序
- 在cmd命令窗口下，使用`gcc or g++`命令来对源代码进行编译链接，生成可执行程序==exe文件==

## 优缺点
虽然使用MinGW可以让您更容易地访问GNU库并将您以前的Linux开发技能移植到Windows，但MSVC将为您提供VS工具，如MFC、ATL、DirectX和GDI+。

使用MinGW还可以让您更好地将软件交叉编译到Linux或Windows上，同时您必须适应MSVC解决方案，通过一些#ifdef或MAKE文件(或另一个构建自动化系统)定制使其在两个平台上都能工作(大多数情况下我会选择后者)。
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTQ4MTEzOTM2MCw1NjY0ODQzOTIsLTExNz
EwODU2MTUsNTE5ODU2MDEyLC02MTEwNTAwMzYsMTgwMzEwMjM0
MF19
-->