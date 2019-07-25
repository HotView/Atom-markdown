tensorboard的使用流程
## Scalar面板
==常量的数据面板==
水平轴有三个参考量
- STEP：代表按照迭代次数
- RELATIVE：代表按照训练集和测试集的相对值
- WALL：代表按照时间

其中面板还会绘制每一层的偏置(biases)和权重(weight),包括每次迭代中的最大值，最小值，平均值和标准差。
## Images面板
==计算机视觉的图片面板==
展示了训练集和测试集经过预处理后图片的样子
## Audio
主要是音频数据的分析
## Graphs面板
直观展示了数据流图，连线越粗，说明两个节点之间流程的张量越多

面板的左侧，可以选择迭代步骤。可以选择使用不同的颜色表示不同的Structure，或者不同的颜色表示不同的设备
## Distributions
使用平面来表示来自特定层的激活前后，权重W和偏置b的分布。
## Histograms
主要是立体的展示来自特定层的激活前后，权重和偏置的分布
## Embedding面板
三维投影可视化一般分为5个步骤
- 读取需要训练的数据
- 创建一个摘要的文件写入符
- 配置一个投影器
- 创建tensorflow会话
- 创建精灵图
- 本地运行tensorboard程序
## 示例1
```py
with tf.name_scope("layer"):
    loss = tf.reduce_mean(tf.reduce_sum(tf.square(ys-prediction),reduction_induces = [1]))
sess = tf.Session()
writer = tf.train.SummaryWriter("logs/",sess.graph)
```
## 示例2
可视化训练过程：Histograms。
横轴为训练的步数的变化。
把整个误差值显示出来：Events
