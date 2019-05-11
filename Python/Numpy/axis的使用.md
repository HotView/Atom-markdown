axis表示坐标轴，不能在序列中使用，只能在ndarray中使用

axis= 0：就表示第一坐标轴
axis = 1：就表示第二坐标轴
依次类推
## 解释1
各个坐标轴的维度大小
- 第一坐标轴的大小就是只考虑第一个方括号内的对象的长度（个数）（ndarry也是一个对象）
- 第二坐标轴的大小就是第二个方括号内的对象的长度（个数）
- 第三坐标轴的大小就是第三个方括号内的对象的长度（个数）
## 解释2
设axis = i，则Numpy沿着第i个下标变化的方向进行操作，操作之后第i个下标消失！
array[index1][index2][...][indexn]
将变化的那些对象对应元素操作，sum就是求和，max就是比大小！

## 广播规则
如果两个数组的shape不相同的话，就在shape属性前面补1，使得其维数相同。


> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTY0NDEwOTg5OSwtMTY5OTg1MzI4MywtNz
IxMTc2MTUzXX0=
-->