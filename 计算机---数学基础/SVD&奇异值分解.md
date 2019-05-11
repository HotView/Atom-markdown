背景：
每一列都可以看做一个特征，每一列的数据的方差可以表示为样本之间在这个特征的差距。如果方差较大，证明这个特征就比较有意义，如果方差很小，说明这个特征就没有很大的意义，对于在一个特征里区分不同的样本。

背景例子
![enter image description here](http://images.cnblogs.com/cnblogs_com/LeftNotEasy/201101/201101192226359750.png)
这个假设是一个摄像机采集一个物体运动得到的图片，上面的点表示物体运动的位置，假如我们想要用一条直线去拟合这些点，那我们会选择什么方向的线呢？当然是图上标有signal的那条线。如果我们把这些点单纯的投影到x轴或者y轴上，最后在x轴与y轴上得到的方差是相似的（因为这些点的趋势是在45度左右的方向，所以投影到x轴或者y轴上都是类似的），如果我们使用原来的xy坐标系去看这些点，容易看不出来这些点真正的方向是什么。但是如果我们进行坐标系的变化，横轴变成了signal的方向，纵轴变成了noise的方向，则就很容易发现什么方向的方差大，什么方向的方差小了。
## 概念
在实数范围内讨论，我们实质上是将一个复杂的变换 M:Rm→Rn 分解成了三个变换：旋转/镜像 U:Rm→Rm、缩放 Σ:Rm→Rn、旋转/镜像 V:Rn→Rn。

**奇异值分解应该就是把一个线性变换分解成两个线性变换，一个线性变换代表旋转，另一个代表拉伸；U和V都起到了对A旋转的作用，而Σ起到了对A缩放的作用。特征值分解只有缩放的效果。**

==一个正交基，经过M变换之后，与另一个正交基的方向一样，两个空间正交基同方向不同长度，乘以$\sum$即同方向，相等。==

该部分是从几何层面上去理解二维的SVD：对于任意的 2 x 2 矩阵，通过SVD可以将一个相互垂直的网格(orthogonal grid)变换到另外一个相互垂直的网格。 我们可以通过向量的方式来描述这个事实: 首先，选择两个相互正交的单位向量  v1和  v2, 向量  Mv1 和  Mv2  正交。

![水平变换效果](http://shartoo.github.io/images/blog/svd8.jpg)

u1和  u2  分别表示  Mv1  和  Mv2 的单位向量，$σ1∗u1=Mv1$  和  $σ2∗u2=Mv2$  。σ1  和  σ2分别表示这不同方向向量上的模，也称作为矩阵M 的奇异值。

![水平变换效果](http://shartoo.github.io/images/blog/svd9.jpg)

这样我们就有了如下关系式：

$Mv_1=σ_1u_1$
$Mv_2=σ_2u_2$

我们现在可以简单描述下经过 M 线性变换后的向量 x 的表达形式。由于向量  v1  和  v2  是正交的单位向量，我们可以得到如下式子

x=(v1x)v1+(v2x)v2

这就意味着：

$Mx=(v_1x)Mv_1+(v_2x)Mv_2$
$Mx=(v_1x)σ_1u_1+(v_2x)σ_2u_2$

向量内积可以用向量的转置来表示，如下所示:

V.x=VTx

最终的式子为:
$Mx=u_1σ_1{v_1}^Tx+u_2σ_2{v_2}^Tx$
$M=u_1σ_1{v_1}^T+u_2σ_2{v_2}^T$


上述的式子经常表示成

$M =U\sum V^T$

u 矩阵的列向量分别是  u1,u2，∑是一个对角矩阵，对角元素分别是对应的  σ1  和  σ2  ，V矩阵的列向量分别是  v1,v2  。上角标T 表示矩阵 V 的转置。

这就表明任意的矩阵 M 是可以分解成三个矩阵。V表示了原始域的标准正交基，u 表示经过M 变换后的co-domain的标准正交基，Σ表示了V 中的向量与u中相对应向量之间的关系。(V describes an orthonormal basis in the domain, and U describes an orthonormal basis in the co-domain, and Σ describes how much the vectors in V are stretched to give the vectors in U.)
## 求解
- 求解U
对$AA^T$做特征分解
- 求解V
对$A^TA$做特征分解
- 求解$\sum$
将第一步或第二步求解的特征值，按从小到大排列。
## SVD按行或列压缩
- 对列压缩
SVD得出的奇异向量也是从奇异值由大到小排列的，按PCA的观点来看，就是方差最大的坐标轴就是第一个奇异向量，方差次大的坐标轴就是第二个奇异向量…我们回忆一下之前得到的SVD式子：
![image](https://images.cnblogs.com/cnblogs_com/LeftNotEasy/201101/201101192226366818.png "image")
在矩阵的两边同时乘上一个矩阵V，由于V是一个正交的矩阵，所以V转置乘以V得到单位阵I，所以可以化成后面的式子
![image](https://images.cnblogs.com/cnblogs_com/LeftNotEasy/201101/201101192226374899.png "image")
将后面的式子与A * P那个m * n的矩阵变换为m * r的矩阵的式子对照看看，在这里，其实V就是P，也就是一个变化的向量。这里是将一个m * n 的矩阵压缩到一个m * r的矩阵，也就是对列进行压缩，如果我们想对行进行压缩（在PCA的观点下，对行进行压缩可以理解为，将一些相似的sample合并在一起，或者将一些没有太大价值的sample去掉）怎么办呢？同样我们写出一个通用的行压缩例子：
- 按行压缩
![image](https://images.cnblogs.com/cnblogs_com/LeftNotEasy/201101/201101192226374060.png "image")
这样就从一个m行的矩阵压缩到一个r行的矩阵了，对SVD来说也是一样的，我们对SVD分解的式子两边乘以U的转置U'
![image](https://images.cnblogs.com/cnblogs_com/LeftNotEasy/201101/201101192226374408.png "image")
这样我们就得到了对行进行压缩的式子。可以看出，其实PCA几乎可以说是对SVD的一个包装，如果我们实现了SVD，那也就实现了PCA了，而且更好的地方是，有了SVD，我们就可以得到两个方向的PCA，如果我们对A’A进行特征值的分解，只能得到一个方向的PCA。



## 最小二乘解优化
目标：min||Ax|| 
约束条件：||x|| = 1
目标函数：||Ax|| 
![enter image description here](https://github.com/HotView/Images/raw/f0bb0e95cc96b8ea655086c46d6703319d6eacab/TIM%E6%88%AA%E5%9B%BE20190325224801.png)
- 令y=$V^Tx$ ,则问题变为：min||Dy|| ；st：||y|| = 1。
- 由于$\sum$是一个对角矩阵，对角元素按降序排列，因此最优解在y=(0,0,...,1)T时取得，又因为$x=Vy$， 所以最优解就是V的最小奇异值对应的列向量，比如，最小奇异值在第6行6列，那么x 为 V的第6个列向量。

当x取最后一列向量时，其对应的奇异值最小，等号成立。因为，x与V的其他的向量点积为零，其他的$\delta_k$都乘以0。

这时，AX的模长取得最小值，也就是在x投影在A空间之后其模长是最小的，也就是离远点最近。
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTUwNzQ0MDg1OV19
-->