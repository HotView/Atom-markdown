## 蛮力算法
$A(x) = a_0+a_1x+a_2x^2+....+a_{n-1}x^{n-1}$
$B(x) = b_0+b_1x+b_2x^2+....+b_{n-1}x^{n-1}$
时间复杂度：O($n^2$)
卷积计算等价于多项式相乘。
## 计算2n-1次多项式C(x)
1. 选择值$x_0，x_1，....，x_{2n-1}$
求出$A(x_j)和B(x_j)$,
j= 0,1，.....，2n-1
2. 对每个j，计算$C(x_j) =A(x_j)B(x_j)$
3. 利用多项式插值方法，由C(x)在$x = x_0,x_1,.....,x_{2n-1}$的值求出多项式C(x)的系数。

问题：如何选择x的取值？高效多项式求值算法。
## 高斯滤波的权值函数
$w_s = \frac{1}{z}e^{-s^{2}}$;s= 0,-+1,-+,2,....,-+k
w = $(w_{-k},...w_{-1},w_0,w_1,....w_k)$
其中z用于归一化处理，使得所有的权值之和为1。
## FFT算法


> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTg0OTAwODU4Ml19
-->