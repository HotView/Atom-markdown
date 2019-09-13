对像素级别做判别，更加真实，语义分割。
信息更加精确。
![](picture/Mask-R-CNN-56983d48.png)
三个loss：Softmax，BBox Reg，RPN。
使用插值，而是直接取整，BBox的值为实数，使得信息变得更准确。
