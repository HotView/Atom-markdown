两个匹配器：
- DMatch = cv2.BFMatcher( )
- DMatch = cv2.FlannBasedMatcher( )

用于匹配键值描述符的类：
- _queryIdx：查询描述符索引
- _trainIdx测试描述符索引
- _imgIdx测试图像索引
- _distance描述符之间的距离。
## 数据结构
```python
cv::DMatch::DMatch	(	int 	_queryIdx,
						int 	_trainIdx,
						float 	_distance 
)		
Python:
<DMatch object>	=	cv.DMatch(		)
<DMatch object>	=	cv.DMatch(	_queryIdx, _trainIdx, _distance	)
<DMatch object>	=	cv.DMatch(	_queryIdx, _trainIdx, _imgIdx, _distance	)

```
```python
cv::DMatch::DMatch	(	int 	_queryIdx,
						int 	_trainIdx,
						int 	_imgIdx,
						float 	_distance 
)		
Python:
<DMatch object>	=	cv.DMatch(		)
<DMatch object>	=	cv.DMatch(	_queryIdx, _trainIdx, _distance	)
<DMatch object>	=	cv.DMatch(	_queryIdx, _trainIdx, _imgIdx, _distance	)

```
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5MzIwOTI3MDNdfQ==
-->