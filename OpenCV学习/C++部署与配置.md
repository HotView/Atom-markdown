以windows下的Opencv为例，解压缩所下载的压缩包会有两个文件夹，分别为“build”和“source”
- source是存放源码的，在其子文件夹“modules”下列出了OpenCV实现的各个模块，其中core，highgui和imgproc是最基础的模块，也是学习的重点。
    - core实现最核心的数据结构及其基本运算
    - highgui实现图像的读取，显示，存储等UI接口
    - imgproc模块实现了图像处理的基础方法，包括几何变换，平滑，形态学处理，边缘检测，频率处理等

## 部署Opencv
配置环境变量，将==动态链接库==的路径添加到path环境变量中去，OpenCV2版本是解压缩路径\build\x64\vc12\bin；OpenCV3版本是解压缩路径\build\x64\vc14\bin添加进去Path系统变量即可。==完成后重启。==

下面是项目配置
- 新建一个Projects，在vs2015中
- 鼠标右键单击工程名称，弹出的快捷菜单选择“Properties”（属性）选项，点击“configuration Properties”--》“VC++ Directories”--》“Include Directories”，接着在弹出的“Include Directories”对话框中将OpenCV的==头文件路径==（..\bulid\include\opencv2）添加进去
- 接下来右键单击“Library Directories”选项，配置==静态链接库==的路径（..\build\x64\vc14\lib）点击ok，至此，OpenCV的头文件和静态链接库的路径配置完成
- 接着依次点击“Linker”（链接器）--》"Input"（输入）---》“Additional Dependencies”（附加依赖项），lib库文件在\build\x64\vc14\lib下，文件名带“d”的lib库是debug模式，不带的是release模式。单击OK，至此，整个工程配置完成。

## 附录
为啥要配置附加依赖项
- 库目录只是查找目录，类似环境变量PATH；具体用哪一个需要指明的，如果不在附加依赖项里填上，就需要在代码里用#pragma comment（lib, “xxx.lib”）来手动指定了。
- 你写代码读写一个文件需要写明文件名吧，这个文件名就相当于那个lib , 但读写这个文件可以不写全路径，就是因为有工作目录(lib只是指明了路径)的存在
