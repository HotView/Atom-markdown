LBP（Local Binary Patterns）
人脸识别，纹理检测，对象检测。
## 介绍
窗口二值化，将中心像素为阈值，将周围领域的像素阈值二值化。
将得到的01序列存储，是每个像素的特征。
- 平坦区：全是0；
- 点：全是1。
- 角点：一个角为0，其余为1。
- 线：部分1或0。
- 边缘：一个角为1，其余为0。

可以设置相应的权重矩阵。鲁棒光照的影响。
## 扩展
多尺度表达：尺度不变性。
邻域范围不断扩大。
#### 也可以实现旋转不变性
## LBP同一模式
没有改变的：u= o。
改变两次的：u = 2。
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTg2OTY5MzQxNV19
-->