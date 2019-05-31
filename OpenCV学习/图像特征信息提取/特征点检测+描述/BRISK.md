BRISK算法是2011年ICCV上《BRISK:Binary Robust Invariant Scalable Keypoints》文章中，提出来的一种特征提取算法，也是一种二进制的特征描述算子。

它具有较好的旋转不变性、尺度不变性，较好的鲁棒性等。在图像配准应用中，速度比较：SIFT<SURF<BRISK<FREAK<ORB，在对有较大模糊的图像配准时，BRISK算法在其中表现最为出色。
## 原理
它的基础也是成对地比较强度值。但有两点不同：
- 它不是从31*31的领域中随机选取像素，而是从一系列等间距的同心圆（由60个点组成）的采样模式中选取
- 这些采样点的强度值都经过高斯平滑处理，处理中使用的$\sigma$值与该像素到圆心的距离成正比
- BRISK据此选取了512对点
#### 特征点检测
BRISK算法主要利用FAST9-16进行特征点检测，要解决尺度不变性，就必须在尺度空间进行特征点检测，于是BRISK算法中构造了图像金字塔进行多尺度表达。
- 建立尺度空间，得到8张图
- 特征点检测
- 非极大值抑制，特征点在位置空间（8邻域）和尺度空间（上下层2*9），共26个点处理
- 亚像素插值，得到精确坐标点
#### 特征点描述
- 高斯滤波
- 局部梯度计算
- 构建同心圆，运用BRIEF描述子来进行描述，进行二进制编码。
#### 匹配方法
汉明距离进行比较，与其他二进制描述子的匹配方式一样。
## OpenCV的使用
- cv2.BRISK.detect(image[, mask])-->keypoints
返回特征点
- cv2.BRISK.compute(image, keypoints[, descriptors])-->keypoints, descriptors
特征点+描述子
- cv2.BRISK.detectAndCompute(image, mask[, descriptors[, useProvidedKeypoints]])-->keypoints, descriptors
- 特征点+描述子
