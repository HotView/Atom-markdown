cv2.calibrateCamera(objectPoints, imagePoints, imageSize, cameraMatrix, distCoeffs[, rvecs[, tvecs[, flags[, criteria]]]]) ! retval, cameraMatrix, distCoeffs, rvecs,  tvecs
- retval：根均方(RMS)重投影误差；计算过程中，使用最后一组标定参数(camera amatrix、distCoeffs、rvecs和tvecs)将三维棋盘点(objectPoints)投影到图像平面中，并比较已知的角位置(imagePoints)，返回投影点与像素点的偏差大小（单位为像素）。


> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMjA3MjU3MTIyOSw1OTMyOTg0NDEsLTExOD
c0ODMwOTVdfQ==
-->