numpy.array数组结构对数组操作进行了很好的优化，它允许一些普通Python列表中不可用的批量操作。这种narray类型-的细节操作对于OpenCV中的图像操作非常方便的。
## 注意事项
- ==索引是先行后列==，针对于ndarry对象。
- 但是点的坐标是先x后y，先是列号再是行号，比如在绘制函数中的pt1 , pt2 等参数。


## 数据类型的运算
一般读入的整型8通道的图像是一个unit8类型的ndarray，当使用数字2乘以该数组，返回的ndarray的数据类型是unit8，如果某个像素值比如200，运算之后超过了unit8的数据范围，Numpy是通过模运算归到unit8范围的，即400%256 = 144，从而转换成为unit8类型，如果将常数改为2.0，返回的ndarray就变为了float64，也就是常数不同，返回的数据类型也会不一样。

对于8bit图对比度增强来说，线形变换计算出的输出值可能要大于255，需要将这些操作截断为255，而不是取模运算，一般是`img[img>255] = 255`,ndarray的成员函数astype的作用是改变ndarray的数据类型。
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEwOTYwNjIyMDhdfQ==
-->
