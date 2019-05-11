背景：
矩阵乘以一个向量就是对向量进行拉长变换。
矩阵对向量的线性变换。
描述好一个变换，那我们就描述好这个变换的主要的变化方向就好。
## 特性
- 任意矩阵都可以分解。
- 拆分为两个正交矩阵 U, V和一个对角矩阵$\lambda$；即$U\Sigma V^T$。
- 将一个矩阵分解为$\sqrt{\lambda_1 }\vec{u_1}(\vec{v_1})^T+\sqrt{\lambda_2 }\vec{u_2}(\vec{v_2})^T$
- 把小的奇异值丢掉，结果不会相差很大（==简化计算==）。
- 噪声通常会产生小的奇异值，丢掉小的奇异值可以==去噪声==。

## 原理
对W进行SVD，首先进行对角化处理(==V和U都是正交矩阵==)：
- $C= W^TW = VDV^T = V\Sigma^T\Sigma V^T =(V\Sigma^TU^T)(U\Sigma V^T)$
- $B= WW^T = UDU^T = U\Sigma^T\Sigma U^T = (U\Sigma^TV^T)(V\Sigma U^T)$

程序实现：
`u,s,vh = np.linalg.svd(A)`
## 作用
特征提取
- 特征值对应的特征向量就是描述这个矩阵变化方向。
- 特征值排列大小就是对变化方向的排序（从主要的变化到次要的变化排列。）

**特征压缩**
- 去除最小的特征值，降维处理。
- 在python中，SVD返回值是`u,s,vh = np.linalg.svd(A)`
- 具体的操作是：对矩阵A（m\*n）进行奇异值分解，得到u,s,vh三个矩阵。u是m*m矩阵，vh是n\*n矩阵。s是按照大小排列好的值。当恢复原矩阵A时，用u矩阵的列==叉乘==vh的行，然后再乘以对应位置的s的标量数值。

**去噪**
- 因为图像中最小的特征值，对图片或者数据整体不起作用，我们可以将特征值小的看做噪声的干扰，直接将其置为0. 



## 应用
在推荐系统中的应用。
- 二维矩阵可以看做是两类事物的关系的描述
![enter image description here](https://github.com/HotView/Images/raw/master/%E4%B8%8B%E8%BD%BD-2019-03-05%2022_45_33.png)
- 比如一个推荐系统的应用
![enter image description here](https://github.com/HotView/Images/raw/master/%E4%B8%8B%E8%BD%BD-2019-03-05%2022_48_25.png)
![enter image description here](https://github.com/HotView/Images/raw/master/%E4%B8%8B%E8%BD%BD-2019-03-05%2022_52_44.png)
在求取一个未知的向量在特征（降维）空间的应用时，只需要将向量投影到特征空间中，如下图所示：
![enter image description here](https://github.com/HotView/Images/raw/master/%E4%B8%8B%E8%BD%BD-2019-03-05%2022_53_22.png)
在特征空间中，寻求最相似的向量（在二维空间中就以点的形式存在。）
向量相似度量方法
- 距离度量
- 角度度量
![enter image description here](https://github.com/HotView/Images/raw/master/%E4%B8%8B%E8%BD%BD-2019-03-05%2022_53_50.png)

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTM3MjUxNzQ0MV19
-->