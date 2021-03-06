Harris算子对角点做出了规范的数学定义，该定义基于强度值在两个互相垂直方向上的变化率，虽然很完美，但是它需要计算图像的导数，而且计算导数非常耗时。

而本次介绍的一种关键点检测算子，叫做FAST(Features from Accelerated Segment),可以快速用来检测关键点，只是用来检测角点。
## 原理概念
FAST(Features from Accelerated Segment Test)算法会在像素周围绘制一个圆，该圆包括16个像素。然后会在每个像素与加上一个阈值的圆心像素值进行比较，若有连续，比加上一个阈值的圆心的像素值还亮或暗的像素，则可认为圆心是角点。
1.  在图像中选择一个要被识别是否为兴趣点的像素pp。 假设它的亮度是$I_p$​。
2.  选取一个合适的阈值$t$。
3.  考虑这个像素周围的16个像素的圆圈。 （见下图）
![](picture/FAST-3744f5d1.png)
4. 如果在这个圆圈（或者说这16个像素）中存在一组（设为m个）连续像素都比$I_p+t$亮或者都比$I_p-t$都暗，那么像素p就是一个角点。
5. 高速测试被用来排除大量非角点。这个测试只检查1,9，5和13四个像素。先检查像素1和9是不是比中间像素亮或暗，然后检查5和13）。如果p是一个角点，那么这四个像素中至少有三个都比$I_p+t$亮或者都比$I_p-t$暗。如果不符合这个特点，那么p就不可能是一个角点。对于通过了这个测试的像素我们才需要检测检测这个圆圈上所有的像素来最终确定它是不是一个角点。这个检测方式本身性能很好，但有几个缺陷：
    -   对于选取$n<12$的情况，这种算法不适用。
	-   像素的选取不是最佳的，因为它的效率取决于查询的顺序和边缘的外观。
	-   高速测试的结果没有在后面的检测中被使用到。
	-   会检测出多个相邻的特征点。

前三个缺陷是用机器学习方法解决的。 最后一个是使用非最大抑制来解决的。
#### 非最大抑制
另一个问题是检测出多个相邻的兴趣点。 这个问题通过使用非最大抑制来解决。

1.  计算所有检测到的特征点的得分函数$V$。 $V$是$p$和16个周围像素值之间绝对差值的总和。
2.  考虑两个相邻的关键点，计算它们的$V$值。
3.  丢弃$V$值较低的关键点。
## OpenCV应用
返回值是关键点，没有描述子，Python中的API接口。
- Python: cv2.FastFeatureDetector([threshold[, nonmaxSuppression]]) ! <FastFeatureDetector object>
- Python: cv2.FastFeatureDetector(threshold, nonmaxSuppression, type) ! <FastFeatureDetector object>
- Python: cv2.FastFeatureDetector.detect(image[, mask]) ! keypoints
## 总结
这种算法比其他已经存在的角点检测算法快数倍。
但这种算法对高水平的噪声敏感。它依赖于一个阈值。

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTgxMTI4NzA0Nl19
-->
