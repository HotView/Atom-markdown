对Harris角点算子的改进，在opencv中实现的函数是==goodfeaturesToTrack==。

它通过考察自相关矩阵M的两个特征值中较小者来确定就角点。

大部分情况下，有比Harris更好的检测效果。
## 理论原理
与harris理论差不多，获取梯度，获取角点响应，阈值来确定。
只是最后一步的角点响应定义不同。
harris检测的角点响应：$R = det(M)-k(trace(M))^2$
托马斯的改进角点响应$R = min(\lambda1,\lambda2)$
## Shi-Tomasi 角点检测器
OpenCV中的函数是`cv2.goodFeaturesToTrack()`
我们首先知道的是Harris角点检测器，在1994年，
Shi and C. Tomasi made a small modification to it in their paper  **Good Features to Track**  which shows better results compared to Harris Corner Detector. The scoring function in Harris Corner Detector was given by:

![R = \lambda_1 \lambda_2 - k(\lambda_1+\lambda_2)^2](https://opencv-python-tutroals.readthedocs.io/en/latest/_images/math/0a3ea39f0c903da7c210e2912e3c51805597f23a.png)

Instead of this, Shi-Tomasi proposed:

![R = min(\lambda_1, \lambda_2)](https://opencv-python-tutroals.readthedocs.io/en/latest/_images/math/1d9c5f834abe53109bc6cfea3557294bb38ba935.png)

If it is a greater than a threshold value, it is considered as a corner.
## OpenCV
cv2.goodFeaturesToTrack(image, maxCorners, qualityLevel, minDistance[, corners[, mask[,  
blockSize[, useHarrisDetector[, k]]]]]) $\rightarrow$ corners

==Parameters==
- image – Input 8-bit or floating-point 32-bit, single-channel image.
- corners – Output vector of detected corners.
- maxCorners – Maximum number of corners to return. If there are more corners than are  found, the strongest of them is returned.  
- qualityLevel – Parameter characterizing the minimal accepted quality of image corners. The parameter value is multiplied by the best corner quality measure, which is  the minimal eigenvalue (see cornerMinEigenVal() ) or the Harris function response  (see cornerHarris() ). The corners with the quality measure less than the product  are rejected. For example, if the best corner has the quality measure = 1500, and the  qualityLevel=0.01 , then all the corners with the quality measure less than 15 are rejected.  
- minDistance – Minimum possible Euclidean distance between the returned corners.
- mask – Optional region of interest. If the image is not empty (it needs to have the type  CV_8UC1 and the same size as image ), it specifies the region in which the corners are  detected.
- k – Free parameter of the Harris detector.

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTQ5NTQxOTIyMF19
-->
