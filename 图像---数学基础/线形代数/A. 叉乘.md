Cross products
叉乘得到向量的长度：表示面积，行列式。
方向垂直于原来两个叉乘的平面。
- 右手准则
逆时针叉乘为正值
顺时针叉乘为负值
## 定义
对于线性无关的两个向量a 和 b ，它们的叉积写作axb，是 a和b所在平面的法线向量，与a和b都垂直，大小是两个向量围成的区域的面积。

#### 计算形式：
对于两个向量v,w。我们将v，w分别组合为一个矩阵A，A的列向量就是v，w，那么A就可以看做是一个对i和j基向量的线性变换，而A的行列式就是对于i，j基向量线性变换之后形成的v，w围成的超体积的大小。
## 推广
向量之间的运算有点积和叉积（Cross Product，向量积、外积），其中点积是比较简单的，而且很容易推广到高维；但是叉积不同，一般来说它只不过是三维空间中的东西。叉积的难以推广在于它的多重含义性，如果将向量及其叉积放到张量里边来看（这属于微分形式的内容），那么三维以上的向量叉积是不存在的；但是如果只是把叉积看成是“由两个向量生成第三个与其正交的向量”的工具的话，那么叉积也是可以高维推广的，而且推广的技巧非常巧妙，与三维空间的叉积也非常相似。
## 回顾三维空间
为了推广三维空间的叉积，首先回顾三维空间的叉积来源是有益的。叉积起源于四元数乘法，但是从目的性来讲，我们希望构造一个向量w=(w1,w2,w3)w=(w1,w2,w3)，使得它与已知的两个不共线的向量u=(u1,u2,u3),v=(v1,v2,v3)u=(u1,u2,u3),v=(v1,v2,v3)垂直（正交）。从普适性的角度来讲，我们还希望构造出来的向量没有任何“奇点”，为此，我们只用乘法构造。至于叉积的几何意义，则是后话，毕竟，先达到基本的目的再说。

这里，为了构造出这样的向量，行列式发挥着巨大作用！我们考虑行列式  


$$\begin{vmatrix}u1&v1&w1\\u2&v2&w2\\u3&v3&w3\end{vmatrix}$$

由行列式的性质可以知道，如果(w1,w2,w3)=(u1,u2,u3)，那么行列式就为0，展开来就是：  

$$u1\begin{vmatrix}u2 &v2 \\u3&v3 \end{vmatrix}-u2\begin{vmatrix}u1 &v1 \\u3&v3 \end{vmatrix}+u3\begin{vmatrix}u1 &v1 \\u2&v2 \end{vmatrix}=0$$

同理，如果((w1,w2,w3)=(v1,v2,v3)，那么行列式也为0，展开来得到  

$$v1\begin{vmatrix}u2 &v2 \\u3&v3 \end{vmatrix}-v2\begin{vmatrix}u1 &v1 \\u3&v3 \end{vmatrix}+v3\begin{vmatrix}u1 &v1 \\u2&v2 \end{vmatrix}=0$$
这样看来，向量  

$$(\begin{vmatrix}u2 &v2 \\u3&v3 \end{vmatrix},-\begin{vmatrix}u1 &v1 \\u3&v3 \end{vmatrix},\begin{vmatrix}u1 &v1 \\u2&v2 \end{vmatrix})$$

  
自动地与向量u=(u1,u2,u3),v=(v1,v2,v3)垂直。而上式就是我们目前定义的向量叉积，因此叉积来源可见一斑。

在理论分析中，我们一般将叉积写成  

$$u×v=\begin{vmatrix}u1&v1&e1\\u2&v2&e2\\u3&v3&e3\end{vmatrix}$$

其中e1,e2,e3是三维空间的基。

## 高维的叉积

有了上面的基础后，高维空间的叉积也就不难定义了，比如说四维空间中的三个向量x=(x1,x2,x3,x4),y=(y1,y2,y3,y4),z=(z1,z2,z3,z4)，它的叉积可以定义为  

$$Cross(x,y,z)=\begin{vmatrix}x1&y1&z1&e1\\x2&y2&z2&e2\\x3&y3&z3&e3\\x4&y4&z4&e4\end{vmatrix}$$
  
高维的空间向量也可以类似定义。

现在来考虑它的模的几何意义。记Cross(x,y,z)=w=(ω1,ω2,ω3,ω4)，其中  

$$w1=\begin{vmatrix}x2&y2&z2\\x3&y3&z3\\x4&y4&z4\end{vmatrix}$$
$$w2=-\begin{vmatrix}x1&y1&z1\\x3&y3&z3\\x4&y4&z4\end{vmatrix}$$
$$w3=\begin{vmatrix}x1&y1&z1\\x2&y2&z2\\x4&y4&z4\end{vmatrix}$$
$$w4=-\begin{vmatrix}x1&y1&z1\\x2&y2&z2\\x3&y3&z3\end{vmatrix}$$


那么行列式  

$$\begin{vmatrix}x1&y1&z1&w1\\x2&y2&z2&w2\\x3&y3&z3&w3\\x4&y4&z4&w4\end{vmatrix}$$

  
就表示x,y,z,w所组成的平行四维体的四维超体积。而且由于w垂直于另外三个向量，那么这个平行四维体其实就是四维空间的一个“四维直棱柱”（想像三维的直棱柱），它的“底部”是由x,y,z所组成的三维空间的平行六面体。根据“体积=底面积乘以高”的类比，上述行列式应该等于“平行六面体的体积乘以w的模长”。当模长为1时，4维柱体的超体积在数值上就等于三维平行六面体的体积。于是行列式  

$$\begin{vmatrix}x1&y1&z1&\frac{w1}{|w|} \\x2&y2&z2&\frac{w2}{|w|} \\x3&y3&z3&\frac{w3}{|w|} \\x4&y4&z4&\frac{w4}{|w|} \end{vmatrix}$$

就等于由x,y,z所组成的三维空间的平行六面体的体积，对最后一列展开它之后就得到|w|。这就是模的几何意义，它和三维空间的叉积类似。更高维空间叉积及其模长的几何意义也可以相应类比，n维空间的(n-1)个线性无关的向量可以定义叉积，它的模长就是原来(n-1)个向量所构成的(n-1)维体的超体积。

回首一看，就可以发现，这个结果甚至对于2维空间都是成立的。由向量(a,b)(a,b)自构造一个叉积，即垂直于它的向量，只需要考虑行列式  

$$\begin{vmatrix}a&e1\\b&e2\end{vmatrix} = -be1+ae2 = (-b,a)$$
可见，叉积为生成垂直向量提供了最自然的描述。

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbNDE4MDM0MDQ5LDM4NDE2MDcxNSwtMTQzNj
gwMjM4LC0yMDQ1MzcwMDc3XX0=
-->