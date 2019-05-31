BRISK并不是唯一的多尺度快速检测器，还有一个ORB特征检测器也能进行关键点的快速检测
ORB：Oriented FAST and Rotated BRIEF

ORB 基本是 FAST 关键点检测和 BRIEF 关键点描述器的结合体
## 原理
ORB代表定向FAST和旋转BRIEF，这个缩写第一层含义表示关键点检测，第二层意思表示ORB算法提供描述子
#### 特征点检测
由FAST来检测关键点
- BRISK一样，首先创建图像金字塔，由一系列图层组成，每个图层用固定的缩放因子对前一层下采样得到
- 然后利用Harris角点的度量方法，从FAST特征点从挑选出Harris角点响应值最大的N个特征点。
#### 特征描述子
rBRIEF是在BRIEF基础上加入旋转因子改进的。
## OpenCV的使用
- cv2.ORB.detect(image[, mask])--> keypoints
特征点
- cv2.ORB.compute(image, keypoints[, descriptors])-->keypoints, descriptors
特征点+描述子
- cv2.ORB.detectAndCompute(image, mask[, descriptors[, useProvidedKeypoints]])-->keypoints,descriptors
特征点+描述子
## 特征匹配
ORB的描述符是二进制的，而SIFT和SURF是浮点型的。要比较ORB的描述符，请使用FLANN+LSH索引或暴力+汉明距离
#### 搭配FLANN
参数设定
```py
FLANN_INDEX_LSH = 6
index_params = dict(algorithm = FLANN_INDEX_LSH,table_number = 6, # 12
                   key_size = 12,     # 20
                   multi_probe_level = 1)#2
search_params = dict(checks=50) # or pass empty dictionary
```
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTU3MjAyMTcyM119
-->
