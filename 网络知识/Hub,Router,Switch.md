前言：
	Hub，Switch，Router三种设备在OSI的最低的三层工作：物理层，数据链路层，网络层。
## HUB（）
hub在第一层（物理层工作）。
广播
when a data ==packet== arrives at one of the ports ,it is copied to all of other ports .
so all the devices on that hub sees that  a data packet comes into one port ,then the hub will just rebroadcast that data to every port that a device connected to it.
转发所有端口！
一个数据包发送到Hub时，Hub将数据包转发到所有的端口。
只能检测一个设备是否物理的连接
## Switch（交换机）
switch工作在第二层：数据链路层。
内部路由，转发到特定端口！

当我们讨论交换机时，是关于它的角色主要功能的，它的主要功能是交换作用。当然他也相当于一台PC，也具备处理物理层数据的能力，但那不是交换机在数据链路层的主角。

一个端口对应一台主机的MAC地址，存储在交换表中。
当一个数据包发送到交换机时，交换机根据目的地来选择目的地端口。
根据mac地址来确定哪个端口转发。

## Router（路由器）
Router工作在第三层：网络层。
交换机和Hub用来在局域网中交换数据（例如家庭，公司）
如果一个子网要和另一个子网交换数据，这将需要路由器。
从一个IP子网络传送到另一个IP子网络！
- 路由器，就像我们在盒子里所说的路由器，就是一台电脑。它运行一个具有网络堆栈的操作系统。路由软件在第三层上运行。底层操作系统有一个网络堆栈，它有一个第二层来处理那些东西，就像你使用的计算机有一个网络堆栈，它有一个第二层，但它们不是交换机。第三层路由器软件把它的数据包交给底层操作系统的网络堆栈的第二层。
- 我想当你谈论这些东西的时候它是关于它的角色的。路由器的作用是路由数据包。当然它有一个网卡来处理第二层的东西，但那不是它在网络上的角色。
![路由功能](https://github.com/HotView/Images/blob/master/TIM%E6%88%AA%E5%9B%BE20190123191129.png?raw=true)

- 当一个数据包发送到路由器时，它会检查数据IP，然后决定这个数据包是发到自己网络中的还是发送到其他网络中的。
- 如果数据发送到它的网络中，它就会接受数据。
- 否则它就会将包发送到其他的网络中。所以路由器中网关是非常重要的。

## 总结
主机-->【交换机，Hub】-->路由器
剩下的就是在路由器上一直转发，直到到达一个路由器，数据包的目的IP就是那个路由器自己的网络，然后这个路由器就把数据包接受了，终止转发！

## 数据传输过程
主机-->【IP Packet】-->【Ethernet Frame】-->Packet-->第一个路由器-->Packet-->Frame-->Packet-->第二个路由器
Processing the Frame
1. Accepting the frame from a medium
2. Decapsulating the frame into a packet
3. Construct a new Frame appropriate for the next media
4. Forwarding the packet inside the new frame across the next segment of the physical network.
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTEwMDc2MjAyNywtMTkzMjMyNTg1NywxOD
c5NDM4MjA1LDEzNzc1NzgzNDQsLTE3MTY2NzA1MjVdfQ==
-->