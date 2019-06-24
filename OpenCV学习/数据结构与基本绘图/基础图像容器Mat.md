在进入OpenCV之后的2.0时代，使用Mat类数据作为主打之后，读写图像就很方便了。
##Mat
Mat是一个类，由两个数据组成部分：矩阵头和一个指向存储所有像素值的矩阵的指针。
## 显示创建Mat的7种方法
- 使用Mat（）构造函数
- 在C++中通过构造函数初始化
- 为已存在的IpIImage指针创建信息头
- 使用Create函数
- 采用eye，zeros，ones等形式
- 为已存在的对象创建信息头
## 输出其他的数据结构
- 二维点：Point2f
- 三维点：Point3f 
- 定义和输出Mat的vector：
```c
vector<float> v;
v.push_back(3)
v.push_back(3)
v.push_back(3)
Mat(v)
```
- 定义和输出Std::vector点
以vector容器存放二维点：vector<Point2f>
## 常用的数据结构
- Point
Point2i，Point，Point_<int>互相等价
- Scalar
颜色表示类，具有四个元素的数组
- Size
尺寸表示类：宽，高
- Rect
矩形表示类：x,y,width,height
