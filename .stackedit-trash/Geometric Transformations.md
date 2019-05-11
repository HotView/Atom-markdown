OpenCV提供两种方法：warpAffine和warpPerspective，使用这两种变换可以实现所有的变换。
- cv2.warpAffine使用2*3的变换矩阵。
	1. 平移
	2. 旋转
	3. 拉伸
- cv2.warpPerspective使用3*3的变换矩阵：即使在变换之后，直线仍然是直线。


> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEzMDAzMjQxMjNdfQ==
-->