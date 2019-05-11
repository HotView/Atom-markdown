## 配置环境变量
添加环境变量Path，将构建好的软件（即build目录下的文件）的bin目录路径添加到环境变量Path中：
D:\OpenCV\build\x64\vc14\bin（vc14对应VS2015）
## 工程包含（include）目录配置
之前看过的好多博文都说“每次新建工程都要重新配置”，其实不用这样麻烦的。
<1> 打开visual studio，新建win32控制台项目,取个名字，比如叫test1，然后选好路径，点确定.点击下一步，勾上空项目那个√。

<4>接着在解决方案资源管理器的【源文件】处右击->添加->新建项，准备在工程中新建一个cpp源文件。

<5>选定C++源文件，取个名字，比如叫“main”，然后点【添加】，那么，一个新的cpp文件就添加到了工程中。

在属性管理器中进行一次配置，就相当于进行了通用的配置过程，以后新建的工程就不用再额外的进行重新配置了。

1. 在菜单栏里面点<视图>--<属性管理器>，那么就会在visual studio中多出一个属性管理器工作区来。
2. 在新出现的“属性管理器”工作区中，点击项目->Debug|X64->Microsoft.Cpp.x64.user（右键属性，或者双击）即可打开属性页面。![enter image description here](https://upload-images.jianshu.io/upload_images/9833335-1ad6fadfa4ffe176.jpg?imageMogr2/auto-orient/strip%7CimageView2/2/w/893/format/webp)
>不管你是32位还是64位操作系统，只用管你用win32编译器还是X64编译器。
其实配置选择什么跟64位还是32位系统没有直接的关系，而是在于你在编译你的程序的时候是使用哪个编译器。
编译器选的是win32，就用x86
编译器选的是X64，就用X64。不过一般情况下，都是用的win32的X86编译器。所以，无论32还是64位操作系统，配置文件最好都选择x86版的
3. 打开属性页面后，就是一番配置了。首先是在【通用属性】 ->【VC++目录】 ->【包含目录】中，添加上
D:\Program Files\opencv\build\include
D:\Program Files\opencv\build\include\opencv
D:\Program Files\opencv\build\include\opencv2 这三个目录。
## 工程库（lib）目录的配置
- 其实这步和上一步差不多，属性管理器”工作区中，点击项目->Debug|Win32->Microsoft.Cpp.Win32.userDirectories（反键属性，或者双击）打开属性页面。
- 接着上步，就是在【通用属性】 ->【VC++目录】 ->【库目录】中，添加上`D:\Program Files\opencv\build\x86\vc10\lib`这个路径。
## 链接库的配置
- 依然是“属性管理器”工作区中，点击项目->Debug|Win32->Microsoft.Cpp.Win32.userDirectories（反键属性，或者双击）即可打开属性页面。【通用属性】 ->【链接器】->【输入】->【附加的依赖项】

- 对于【OpenCV 3.0】，添加3.0版本的lib，新版的lib非常简单。想用debug版本的库，添加
opencv_ts300d.lib
opencv_world300d.lib 这两个库即可。
而想用release版本的库，添加
opencv_ts300.lib
opencv_world300.lib即可。
其实，对已经发行和未来即将发布的新版OpenCV，只需看opencv\build\x86\vc10\lib下的库是哪几个（文件类型：Object File Library (.lib)），添加成依赖项就可以了。

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTUzNzQ2OTc0Nl19
-->