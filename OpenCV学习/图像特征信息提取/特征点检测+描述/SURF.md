SURF是OpenCV的一个类，了解这一点很重要，SURF采用Hessian算法检测关键点，而SIFT采取DOG算法提取关键点，相对来说SIFT取得更加精确的定位，但是它的计算效率很低。

SURF算法是SIFT算法的加速版
## 原理
- 检测特征点：快速Hessian
- 描述子：使用64维向量来描述
## 程序
```python
surf = cv2.xfeatures2d.SURF_create(8000)  
keypoints,descriptor = surf.detectAndCompute(gray,None)
```
上述采用的Hessian阈值为8000。阈值越高，能识别的特征就越少，因此，可以采用试探法得到最优检测。
==可以创建一个滑动条（trackbar）用来为SURF实例提供Hessian阈值，可以看到特征随阈值的增加而减少。==

## 匹配方法
暴力匹配器，距离度量cv2.NORM_L2

第二个参数是布尔变量，crossCheck默认是false，如果它是true，匹配器返回那些和(i, j)匹配的，这样集合A里的第i个描述子和集合B里的第j个描述子最匹配。两个集合里的两个特征应该互相匹配，它提供了连续的结果。

当它创建以后，两个重要的方法是BFMatcher.match()和BFMatcher.knnMatch()。第一个返回最匹配的，第二个方法返回k个最匹配的，k由用户指定。当我们需要多个的时候很有用。

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEyNjk5MTQzNTNdfQ==
-->
