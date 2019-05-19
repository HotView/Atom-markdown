## imread
cv2.imread(filename , flags)
flags的参数说明：
- IMREAD_ANYCOLOR = 4
- IMREAD_ANYDEPTH = 2
- IMREAD_COLOR = 1
- IMREAD_GRAYSCALE= 0
- IMREAD_LOAD_GDAL = 8
- IMREAD_UNCHANGED = -1
## 色彩空间
- RGB：常见
- HSV：HSV即色相，饱和度，明度。常见H:0-180 S:0-255 C:0-255，某一个颜色出现在特征物体时，可以考虑使用这个。
inrange提取颜色，适用于==颜色物体的跟踪很有用！==
![enter image description here](https://img-blog.csdn.net/20160526140204634?watermark/2/text/aHR0cDovL2Jsb2cuY3Nkbi5uZXQv/font/5a6L5L2T/fontsize/400/fill/I0JBQkFCMA==/dissolve/70/gravity/Center)
- HIS：强度和饱和度
- YCrCb：肤色检测
- YUV：常见（arduino开发）
默认通道是BGR（blue，green，red）。
（matplot是RGB）
## 通道操作
b , g , r  = cv2.split( image )  
cv2.merge( [ b , g , r ] )
## imshow
显示一个图像在确定的窗口中，如果窗口创建的类型是CV_WINDOW_AUTOSIZE，怎窗口可以变换大小。

在浮点图像上进行操作是很常见的。如果使用imshow显示这幅图像，将不会看到任何有意义的内容。在这种情况下，必须将像素转换到0-255整数范围。
- 如果图像是8-bit unsigned，直接显示
- 如果图像是无符号16位或者32位整型，像素值除以256，归一化到【0-255】之后再进行显示。
- 如果图像是32位浮点型，像素值乘以255，然后再进行显示，映射到【0,255】
- 如果像素值为负的话，应该加上某个值，使其全为整数，可以整个图片减去最小值全部变为正数，然后再对其进行归一化，如果是浮点型的就归一化到（0,1），如果是整数就归一化到（0,255）
- 8位整型值的范围是-128~127

## imwrite
`cv2.imwrite(filename，object)`
## copy（）
`img_copy= img.copy()`：用来复制图像。
## raw bytes
```
class bytearray(object)
 |  bytearray(iterable_of_ints) -> bytearray
 |  bytearray(string, encoding[, errors]) -> bytearray
 |  bytearray(bytes_or_buffer) -> mutable copy of bytes_or_buffer
 |  bytearray(int) -> bytes array of size given by the parameter initialized with null bytes
 |  bytearray() -> empty bytes array
 |  
 |  Construct a mutable bytearray object from:
 |    - an iterable yielding integers in range(256)
 |    - a text string encoded using the specified encoding
 |    - a bytes or a buffer object
 |    - any object implementing the buffer API.
 |    - an integer
```
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTMwMzgzMzgzMSwxNTE4MjExMjAxLDIyNT
U4NTM4OSw4Mjc3OTYyOTFdfQ==
-->
