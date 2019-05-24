## 特征描述子的提取（梯度直方图）（Histogram of Oriented Gradients）
- 灰度图像转换
- 梯度计算，计算x，y方向的梯度，然后通过x，y来计算其他方向的幅值和梯度。
- 分网格形成cell，一个cell是8*8大小，然后将一个cell的方向直方图计算出来，分成9个bin，代表9个梯度方向；角度取值范围为-180~180，根据方向选择用哪个bin, 根据副值来确定这个bin的大小。
- 块描述子：将2*2的cell组合成一个block。
- 块描述子归一化：
- ==特征数据与检测窗口==。
- ==匹配方法==。

## 梯度计算
sobel算子
## 分网格的梯度方向直方图
## 例子
一个64*128的像素块，可以分为8*16的cell，分为7*15个块（R-HOG），总计的直方图向量数为：7*15*2*9 = 3780个向量数组


> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTgzOTEyMjM3MywxNTk1MDgxNjI4LC0xNT
IzMTY5NjcxLDEyODk0NjEyMjAsMjEyMDIzMDU4N119
-->