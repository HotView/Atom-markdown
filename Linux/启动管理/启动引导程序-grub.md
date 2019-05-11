grub中的设备文件：hd（0 , 0），hd（0 , 1），hd（0 , 2），hd（0 , 4），hd（1, 0）
grub的配置文件在：/boot/grub/grub.conf
两个部分：整体部分；操作系统部分
## 整体配置
default= 0 ；默认启动第一个操作系统
timeout = 5；选择时间为5秒。
背景图像splashimage
hiddenmenu：启动界面隐藏
## grub配置
title。
root：系统所在分区位置。
kernel：
initrd：
先装Windows，后装Linux；（Linux的grub能够识别Windows。）

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMzAwODQ1OTAzXX0=
-->