全卷积神经网络FCN
- 语义分割
- FCN---》segNet/DeconvNet---》DeepLab
- 目的：语义推断，分割更为精确。
- 工业应用：辅助驾驶
## FCN
反卷积，将AlexNet的网络的最后三层全连接层变为三层卷积层。
上采样卷积。
## SegNet
反池化，设计对称结构。
![](picture/FCN-f09065ed.png)
## DeepLab
膨胀卷积
![](picture/FCN-f80dc7e9.png)
