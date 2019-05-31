角点探测器的数据结构
类实例存储一个关键点，即由许多可用的关键点检测器(如Harris corner检测器、FAST、StarDetector、SURF、SIFT等)之一发现的点特征。
## 数据结构
example1：
```python
cv::KeyPoint::KeyPoint	(	Point2f 	_pt,
							float 	_size,
							float 	_angle = -1,
							float 	_response = 0,
							int 	_octave = 0,
							int 	_class_id = -1 
)		
Python:
<KeyPoint object>	=	cv.KeyPoint(		)
<KeyPoint object>	=	cv.KeyPoint(	x, y, _size[, _angle[, _response[, _octave[, _class_id]]]]	)

Parameters
_pt	    x & y coordinates of the keypoint
_size	keypoint diameter
_angle	keypoint orientation
_response	keypoint detector response on the keypoint (that is, strength of the keypoint)
_octave	pyramid octave in which the keypoint has been detected
_class_id	object id
```
example2：
```python
cv::KeyPoint::KeyPoint	(	float 	x,
							float 	y,
							float 	_size,
							float 	_angle = -1,
							float 	_response = 0,
							int 	_octave = 0,
							int 	_class_id = -1 
)		
Python:
<KeyPoint object>	=	cv.KeyPoint(		)
<KeyPoint object>	=	cv.KeyPoint(	x, y, _size[, _angle[, _response[, _octave[, _class_id]]]]	)


Parameters
x	x-coordinate of the keypoint
y	y-coordinate of the keypoint
_size	keypoint diameter
_angle	keypoint orientation
_response	keypoint detector response on the keypoint (that is, strength of the keypoint)
_octave	pyramid octave in which the keypoint has been detected
_class_id	object id
```
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTU0NzExMDQ4NV19
-->