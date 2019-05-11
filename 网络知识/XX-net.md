一般遇到的问题就是如下的问题：

- 首先是否有ipv6的地址，如果有原生的ipv6则可以直接连接。

-  如果没有原生的ipv6的话，可以使用teredo隧道。用teredo隧道的，确定teredo是否可用，ping值高不高等。

-  AppID申请，然后在gcp上创建项目，创建实例，获取得到appid。
- 最后在xx-net的==部署服务端==选项上进行部署，或者（在SDK上进行部署）

## 使用teredo连接IPv6的设置
- 首先测试teredo是否能够ping的通
- 在ping的通的情况下，手动设置Teredo服务器，然后，打开XX-net看是否能够连接的上。
## 修改设置teredo服务器
- 电脑上手动修改teredo服务器之后，之后是不会变化的。
## 修改xx-net的teredo服务器地址列表
- 根目录-->code-->default-->gae_proxy-->local--> ipv6-tunnel-->pteredo.py
- 修改完之后，删除已经预编译好的文件，然后保存，重新启动start.bat文件即可。
## 问题
1. 在xx-net中，teredo服务器状态显示已经连接，但是ipv6状态failed。
说明teredo的连接情况比较差，可以尝试ping 下连接的teredo服务器，如果超时，证明连接情况很差，可以尝试换一个teredo服务器，之后重启xx-net


> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTIyOTA4MDU0OCwtNzg5NTE0NywxODQ3MD
E3MTQ1XX0=
-->