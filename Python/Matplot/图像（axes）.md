## add_subplot
ax1 = fig.add_subplot(211)：添加图像到窗口。
输出为图像对象。

ax1 = fig.add_subplot(221）
ax1 = fig.add_subplot(222)
ax1 = fig.add_subplot(212)
生成一个

## subplots
输入值：多少行，多少列的axes对象。
输出量：窗口对象，子图对象列表。
```py
img = cv2.imread('test.jpg',0)  
_,ax = plt.subplots(3,4)  
ax4 = ax[1][2]  
ax4.imshow(img)
```
## subplots2grid（）
输入值：为figure对象，（rows，cols），起始位置（x，y），所占用的起始位置（rowspan，colspan）
返回值：图像对象axes。
- 分成三等分的窗口格子
ax1 = plt.subplot2grid((6,1),(0,0),rowspan = 2,colsapn = 1)
ax1 = plt.subplot2grid((6,1),(2,0),rowspan = 2,colsapn = 1)
ax1 = plt.subplot2grid((6,1),(4,0),rowspan = 2,colsapn = 1)
- 自定义三个格子的大小
ax1 = plt.subplot2grid((6,1),(0,0),rowspan = 1,colsapn = 1)
ax1 = plt.subplot2grid((6,1),(1,0),rowspan = 4,colsapn = 1)
ax1 = plt.subplot2grid((6,1),(5,0),rowspan = 1,colsapn = 1)
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2ODQ0MTcwNjFdfQ==
-->