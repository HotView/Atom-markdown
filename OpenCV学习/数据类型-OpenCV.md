## 基本数据类型
结构|成员|意义
---|---|--
CvPoint|int x,y|图像的点
CvPoint2D32f|float x,y|二维点
CvPoint3D32f|float x,y,z|三维点
CvSize|int width,height|图像的尺寸
CvRect|int x,y,width,height|图像的部分区域
CvScalar|double val[4]|RGBA值

## 大小和索引
shape：高，宽
size：宽，高 ，Size_(width,height);
Mat矩阵索引：先行后列
点坐标：先列后行
## 矩阵和图像类型
- OpenCV中没有向量结构。任何时候需要向量，都只需要一个列矩阵
- OpenCV的矩阵元素并非只能取数值类型，可以是其他对象。

矩阵：CvMat
## C++中的数据单元
cv::Mat有两个不可少的组成部分：一个头部和一个数据块。头部包含了矩阵的所有相关信息（大小，通道数量，数据类型等），可以通过（cols，rows，channels）。数据块包含了了图像所有像素的值。头部有一个指向数据块的指针，即data属性。

cv::Mat有一个很重要的属性，即只有在明确的要求是，内存块才会被复制。实际上，大多数的操作仅仅复制了cv::Mat的头部，因此多个对象指向同一个数据块。(这种内存管理模式可以提高应用程序的运行效率，避免内存泄漏，但是我们必须了解它带来的)

//所有图像都指向同一个数据块
cv：Mat image4（image3）
image1 = image3；

//图像的新副本
image3.copyTo( image2 )
cv::Mat image5 = image3.clone();

//如果需要把一幅图像复制到另一幅图像中，且两者数据类型不一定相同，那就要使用convertTo（）方法了
image1.converTo(image2 , CV_32F , 1/255.0 , 0.0);   缩放比例和偏移量（需要注意的是，两幅图像的通道数量必须相同。）
## 数据类型
==CV_【位数】【符号\类型】C【通道数】==
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTAzNTA0MTU0MF19
-->
