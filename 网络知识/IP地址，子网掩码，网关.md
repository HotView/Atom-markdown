每一台设备都有一个掩码：
掩码来控制自己的发送的IP地址能否发送出去！
## subnet mask
Network or Node
computer or router to determine the IP address portion that is for the  
- class A:255.0.0.0；前八位匹配
- class B:255.255.0.0；前16位匹配，LAN Range：192.168.xxx.xxx
- class C:255.255.255.0；前24位匹配，LAN Range：192.168.10.xxx
或者0,128,224,240,248,252,254,255 【easy flags】

问题：how does a device Know to connect on the LAN or ==Through the Gateway（to the WAN）==？
用来判断两台计算机IP地址是否同属于同一子网络。将两台计算机IP与子网掩码做与运算，如果得到的结果相同，就在同一子网，如果不同则不再同一子网，则就可以通过网关。
##  Router
- 路由器也相当于一台PC
- 路由器有两个IP地址：一个是在local area network，例如：192.168.0.1；另一个是wide area network，例如：92.65.46.51
## Gateway
- Gateway 就是路由器的IP地址，如果想要连接外部的网络，就得通过网关。
- 如果网络A中的主机发现数据包的目的主机不在本地网络中，就把数据包转发给自己的网关，再由网关转发给Wide area network。然后路由器再判断是否属于自己的内网的，如果属于，就接收，不属于就继续转发！










> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTk3ODIwOTA3XX0=
-->