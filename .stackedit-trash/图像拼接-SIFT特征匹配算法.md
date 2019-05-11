## 试验方法：
#### sift进行特征提取：
```python
sift = cv2.xfeatures2d.SIFT_create()  
# find key points  
kp1, des1 = sift.detectAndCompute(img_right,None)
```
####  应用暴力匹配器进行knn匹配：
```python
match = cv2.BFMatcher()  
matches = match.knnMatch(des1,des2,k=2)
```
####  寻找好的匹配对应点：
```py
good = []  
for m,n in matches:  
    if m.distance < 0.3*n.distance:#系数以实际情况可调。  
        good.append(m)
```
####  计算两幅图像的单应性变换矩阵：
```py
MIN_MATCH_COUNT = 10  
if len(good) > MIN_MATCH_COUNT:  
    src_pts = np.float32([ kp1[m.queryIdx].pt for m in good ]).reshape(-1,1,2)  
    dst_pts = np.float32([ kp2[m.trainIdx].pt for m in good ]).reshape(-1,1,2)  
  
    M,mask = cv2.findHomography(src_pts, dst_pts, cv2.RANSAC, 5.0)
```
####  通过透视变换，寻找拼接边缘：
```py
h,w = img_right_gray.shape  
pts = np.float32([ [0,0],[0,h-1],[w-1,h-1],[w-1,0] ]).reshape(-1,1,2)  
dst = cv2.perspectiveTransform(pts, M)  
img2 = cv2.polylines(img_left_gray,[np.int32(dst)],True,255,3, cv2.LINE_AA)
```
####  通过仿射变换，得到拼接图像：
```py
dst = cv2.warpPerspective(img_right ,M,(img_left.shape[1] + img_right.shape[1], img_left.shape[0]))  
dst[0:img_left.shape[0],0:img_left.shape[1]] = img_left
```
## 结果
经试验验证：
在进行图像拼接时，在系数为0.65，0.5，0.4，0.3特征点的对数即good的长度为：408，161，69，14时。
==效果最好的是69，其拼接的效果最好。==


> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTUwMzgxMjI5OF19
-->