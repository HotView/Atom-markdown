## 概念
OpenCV中的特征描述符匹配器具有公共接口的包装器，可以在解决相同问题时使用不同算法。
匹配器的公有算法
- add
添加描述符到CPU或者GPU的描述符集合中，如果集合不为空，新的描述符被添加到现有的训练描述符中
- getTrainDescriptors
返回到训练描述符集合traindescollection的常量链接。
- clear
清除训练描述符集合。
- empty
如果两个集合中都没有训练描述符，则返回true。
- isMaskSupported
如果描述符匹配器支持屏蔽允许的匹配，则返回true。
- train
训练描述符匹配程序
- match
`match(InputArray queryDescriptors, InputArray trainDescriptors, vector<DMatch>& matches, InputArray mask=noArray() )`
从查询集中为每个描述符找到最佳匹配。
匹配一对组好的点，返回的对象元素是一个DMatch对象。
- knnMatch
从查询集中为每个描述符找到k个最佳匹配项。匹配K组最好的点，返回的对象元素是K个DMatch对象。
`knnMatch(InputArray queryDescriptors, InputArray trainDescriptors, vector<vector<DMatch>>& matches, int k, InputArraymask=noArray(), bool compactResult=false )`
- radiusMatch
对于每个查询描述符，查找不超过指定距离的训练描述符。
- clone
克隆的匹配器
- create
使用默认参数(使用默认构造函数)创建给定类型的描述符匹配器。
    - BruteForce
    - BruteForce-L1
    - BruteForce-Hamming
    - BruteForce-Hamming(2)
    - FlannBased
## 匹配器种类
BFMatcher( )
FlannBasedMatcher( )
## 返回值DMatch对象
用于匹配键值描述符的类：
- queryIdx：查询描述符索引
- trainIdx测试描述符索引
- imgIdx测试图像索引
- distance描述符之间的距离。

数据结构
```py
C++
cv::DMatch::DMatch	(
int 	_queryIdx,
int 	_trainIdx,
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
