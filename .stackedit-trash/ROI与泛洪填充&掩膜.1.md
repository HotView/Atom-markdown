## ROI
face = src[50:250 , 100:300]
gray = cv2.cvtColor(face,cv2.COLOR_GRAY2BGR)
src[50:250 , 100:300] = gray
## 泛洪填充
一定区域内填充某个颜色值。
==在使用cv2.floodFill( )填充时，mask矩阵中只有像素值为0的地方才会被填充！==
flags模式选择：
- cv2.FLOODFILL_FIXED_RANGE  ：改变图像，泛洪填充
- cv2.FLOODFILL_MASK_ONLY：不改变图像，只填充掩膜本身，忽略新的颜色值参数。
## 掩膜
掩膜操作就是两幅图像的位运算操作。
-   提取感兴趣区,用预先制作的感兴趣区掩模与待处理图像相乘,得到感兴趣区图像,感兴趣区内图像值保持不变,而区外图像值都为0。
位运算与
-   屏蔽作用,用掩模对图像上某些区域作屏蔽,使其不参加处理或不参加处理参数的计算,或仅对屏蔽区作处理或统计。
-  结构特征提取,用相似性变量或图像匹配方法检测和提取图像中与掩模相似的结构特征。
-   特殊形状图像的制作。

 

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5MTgyMTU5NDRdfQ==
-->