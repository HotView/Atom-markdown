主要是想介绍下常用的几种卷积神经网络。卷积神经网络最初为解决图像识别问题而提出，目前广泛应用于图像，视频，音频和文本数据，可以当做深度学习的代名词。
1. 目前图像分类中的ResNet
2. 目标检测领域占统治地位的Faster R-CNN
3. 分割中最牛的Mask-RCNN, UNet和经典的FCN

都是以下面几种常见网络为基础。
- LeNet
- AlexNet
- VggNet
- GoogLeNet
- ResNet
## 工程技巧
- 图像像素中心化
- 梯度剪切
- 权重衰减
- 防止过拟合
## CNN设计准则
- 避免信息瓶颈
- 通道数量
- 感受野足够大
- 分组策略
- 低秩分解
## 区域卷积神经网络
- 第一阶段：R-CNN--》SPP-Net--》Fast/Faster R-CNN
- 第二阶段：YOLO--》SSD--》R-FCN

目的：检测更快，更准确。
智能监控，辅助驾驶。
