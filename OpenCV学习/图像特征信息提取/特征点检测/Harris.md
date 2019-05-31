Harris不止考察水平，垂直4个方向上的灰度差异，而是考察了所有方向的灰度差异，并且具有旋转不变形和对部分仿射变换的稳定性。
## 理论原理
- 定义响应输出：$E(u,v) = \sum w(x,y)[I(x+u,y+v)-I(x,y)]^2$
- w表示窗口大小
- 对上式进行泰勒展开：$E(u,v) = \sum u^2{I_x}^2+2uvI_xI_y+v^2{I_y}^2$
用矩阵来进行相乘：
$$
E(u,v) = \begin{bmatrix}
u &v
\end{bmatrix}M\begin{bmatrix}
u\\
v
\end{bmatrix}
$$
其中M为窗口下的黑塞矩阵的点积，k为经验值在0,04-0.06之间。
角点响应：$R = det(M)-k(trace(M))^2 = \lambda1\lambda2-k(\lambda1+\lambda2)^2$
根据R值来判断是否为角点
## 缺点
如果减小或者增大图像的大小，可能会丢失图像的某些部分，甚至有可能增加角点的质量。

==特征损失现象需要一种与图像比例无关的角点检测方案来解决。也就是尺度不变特征变换（Scale-Invariant Feature Transform）SIFT。==


> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbNDM5NTY0ODc0XX0=
-->
