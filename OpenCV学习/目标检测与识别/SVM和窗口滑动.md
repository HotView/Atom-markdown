在完成目标检测的基础上，增加一些功能：
- 检测图像中同一物体的多个目标。
- 确定检测到的目标在图像中的位置。

## 滑动窗口
- 选择图像区域，对其进行分类，然后向右移动固定大小的一步。当到达图像的最右端时，将x坐标设为0，然后向下移动一步，并重复整个过程。
- 在每步中使用通过BOW训练好的SVM进行分类
- 将所有块传递给SVM进行预测，并保持结果
- 完成整个图像的分类，缩放图像并重复整个滑动窗口的过程。

## 示例
汽车检测的例子：
- 获取一个训练数据集
- 创建BOW训练器并获取视觉单词
- 采用词汇训练SVM
- 尝试对测试图像的金字塔采用滑动窗口进行检测
- 对重叠的矩形使用非最大抑制
- 输出结果
