
## SS配置
进入root权限，运行以下命令：
>wget --no-check-certificate -O shadowsocks-libev.sh https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocks-libev.sh
chmod +x shadowsocks-libev.sh
./shadowsocks-libev.sh 2>&1 | tee shadowsocks-libev.log
## SSR远端服务器配置
- 得到sahdowsocksR.sh文件
wget --no-check-certificate https://raw.githubusercontent.com/teddysun/shadowsocks_install/master/shadowsocksR.sh && chmod +x shadowsocksR.sh
```
echo "#===========================================================#"
echo "# One Click Install ShadowsocksR Server for CentOS & Debian #"
echo "# Github: https://github.com/uxh/shadowsocks_bash           #"
echo "# Thanks: https://github.com/teddysun/shadowsocks_install   #"
echo "#===========================================================#"
```
- 运行这个.sh
bash shadowsocksR.sh
- 配置密码和端口，加密格式
省略
- 安装成功
得到自己的配置信息
## 安装TCP加速软件
`uname -r`
1、结果以 2 开头，例如 2.6.32-696.18.7.el6.x86_64。
这种输出结果说明我们的服务器为 CentOS6 x64 系统，大家直接查看第三步进行锐速安装即可。
`wget --no-check-certificate -O appex.sh https://raw.githubusercontent.com/0oVicero0/serverSpeeder_Install/master/appex.sh && bash appex.sh install '2.6.32-642.el6.x86_64'`
2、结果以 3 开头，例如 3.10.0-693.11.6.el7.x86_64。
这种输出结果说明我们的服务器为 CentOS7 x64 系统，大家直接安装对应的包即可`wget --no-check-certificate -O rskernel.sh https://raw.githubusercontent.com/uxh/shadowsocks_bash/master/rskernel.sh && bash rskernel.sh`
3、结果以 4 开头，例如 4.12.10-1.el7.elrepo.x86_64。
这种输出结果说明我们的服务器已经安装 Google BBR 拥塞控制算法，此时已经无法继续安装锐速。
- 得到安装锐速
先重启服务器，然后继续输入以下命令：
`yum install net-tools -y && wget --no-check-certificate -O appex.sh https://raw.githubusercontent.com/0oVicero0/serverSpeeder_Install/master/appex.sh && bash appex.sh install`
系统会自动安装锐速。之后设置三项信息，全部默认之后，即安装成功。开机自启动。
## google BBR

在上网高峰期来临时，连接速度会比较慢，所以我们有必要安装一些程序来加速连接速度，目前比较热门的Google BBR拥塞控制算法，分为原版和魔改版两个版本，魔改版效果比较好一些。

1. 安装Goolge BBR需要升级系统内核，而安装锐速则需要降低系统内核故两者不能同时安装。

2. 安装Google BBR需升级系统内核，有可能造成不稳定，故不建议将其应用在重要的生产环境中
3. 原版和魔板在不同地区的服务器上会有不同的效果，具有孰优孰劣请分别安装进行测试。

### BBR原版安装
在xshell软件，鼠标右击选择粘贴，回车继续。
`wget --no-check-certificate https://github.com/teddysun/across/raw/master/bbr.sh && chmod +x bbr.sh && ./bbr.sh`
下载脚本之后，脚本执行会显示系统内核版本，回车确认安装即可
当脚本安装之后，询问我们是否重启服务器，我们输入y重启，然后按回车即可。
确认重启之后，我们重新链接服务器即可。
然后运行以下命令
`sysctl net.ipv4.tcp_available_congestion_control`
执行后输出值需为：net.ipv4.tcp_available_congestion_control = reno cubic bbr。
`sysctl net.ipv4.tcp_congestion_control`
执行后输出值需为：net.ipv4.tcp_congestion_control = bbr。
`sysctl net.core.default_qdisc`
执行后输出值需为：net.core.default_qdisc = fq。
以上三条命令的输出值正确后则说明原版 Google BBR 已经成功安装并开机自启动。
### BBR魔板安装
文章开头也说明了魔改版 Google BBR 是在原版 Google BBR 的基础上修改了一些参数，所以两者的性能会有所不同，具体效果则需要大家可以分别进行测试。
PS：魔改版 Google BBR 和 原版 Google BBR 不能够共存的，不要同时安装。

按照《Windows 使用 Xshell 软件连接 Vultr VPS 教程》连接服务器，按照下图提示，我们首先复制命令：

CentOS 6/7 x64 系统请用这个
`wget --no-check-certificate https://raw.githubusercontent.com/nanqinlang-tcp/tcp_nanqinlang/master/General/CentOS/bash/tcp_nanqinlang-1.3.2.sh && bash tcp_nanqinlang-1.3.2.sh`

Debian 7/8 x64 系统请用这个
`wget --no-check-certificate https://github.com/nanqinlang-tcp/tcp_nanqinlang/releases/download/3.4.2.1/tcp_nanqinlang-fool-1.3.0.sh && bash tcp_nanqinlang-fool-1.3.0.sh`
然后回到 Xshell 软件，鼠标右击选择粘贴，回车继续。

回车后系统会自动下载脚本并运行。按照下图提示，我们首先输入“1”（即升级内核），然后回车继续。
回车后系统会自行执行升级内核命令，当出现下图所示信息时，我们输入“y”，然后回车即可继续安装。
安装新内核完成后，按照下图提示，我们输入“reboot”，然后回车即可重启服务器以应用新内核。

确认重启后，Xshell 软件会断开连接。等待 3~5 分钟服务器即可重启完毕，我们重新连接服务器，按照下图提示，我们继续复制命令：
- CentOS 6/7 x64 系统请用这个
`bash tcp_nanqinlang-1.3.2.sh`
- Debian 7/8 x64 系统请用这个
`bash tcp_nanqinlang-fool-1.3.0.sh`
然后回到 Xshell 软件，鼠标右击选择粘贴，回车继续。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190115164728304.png)
回车后系统会自动运行脚本。按照下图提示，我们输入“2”（即开启魔改版 Google BBR 算法），然后回车继续即可。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190115164651575.png)

回车后系统会自行执行开启算法命令，当出现下图所示信息时，我们输入“y”，然后回车即可继续开启。
![在这里插入图片描述](https://img-blog.csdnimg.cn/2019011516464197.png)
当出现下图所示信息时代表魔改版 Google BBR 已经成功安装并开机自启动。
![在这里插入图片描述](https://img-blog.csdnimg.cn/20190115164630473.png)

## 查看修改VPS状态
- 如何查看SS服务器所的端口？
` ss  –lntp  |  grep ssserver`
`ps aux  |  grep ssserver`：列出目前所有的正在内存当中的程序
- 如何查看当前ss服务器的密码？
通过以下命令即可查看ss的配置文件，配置文件中包含有密码：
- cat查看下配置文件，就可以看见密码啦：
` cat  /etc/shadowsocks.json`

- 如何修改SS服务器密码？
运行以下命令：
` vi  /etc/shadowsocks.json`
按【i】键直接进入编辑模式，然后即可修改密码，如修改为：123456
“password”:“123456”
然后重启SS服务器：
`service shadowsocks restart`
## SS使用命令：
启动：/etc/init.d/shadowsocks start
停止：/etc/init.d/shadowsocks stop
重启：/etc/init.d/shadowsocks restart
查看状态：/etc/init.d/shadowsocks status
### service命令
-   服务名：自动要控制的服务名，即`/etc/init.d`目录下的脚本文件名；
- 基本命令启动：service shadowsocks start  
- 停止：service shadowsocks stop  
- 重启：service shadowsocks restart  
- 状态：service shadowsocks status
## ServerSpeeder 锐速服务器加速软件常用命令说明

使用serverSpeeder 服务进行锐速的启动，停止，以及重新加载配置等操作；各参数说明如下：

`service serverSpeeder start`  
：启动锐速，加载加速模块；使用/serverspeeder/etc/config 文件中的配置作为模块加载时的初始化参数；

`service serverSpeeder stop`  
：停止锐速，卸载加速模块；停止锐速前请确认没有其它进程在访问/proc/net/appex/目录，例如确认控制台当前目录是否是/proc/net/appex/；

`service serverSpeeder reload`  
： 在 不 停 止 锐 速 运 行 的 情 况 下 实 时 修 改 锐 速 参 数 配 置 ， 修 改/serverspeeder/etc/config 文件的配置后运行此命令，此时加速模块不退出，参数被实时修改；

`service serverSpeeder restart`  
：重启锐速；

`service serverSpeeder status`  
：查看当前锐速的实时运行状态；授权状态到期时间，版本号，系统序列号，加速连接数，加速速率，配置信息等；

`service serverSpeeder stats`  
：实时显示每个加速引擎的连接数、流量，以及所有引擎的总的连接数和流量；其中连接数统计包括网络连接数(sessions)，tcp 连接数(tcp sessions)，已加速的 tcp 连接数(accelerated sessions)以及活动的 tcp 连接数(active tcp sessions)；流量统计包括流入(in)流量统计和流出(out)流量统计，单位均为 kbit/s；一般情况下，所有引擎的总连接数及流量即为服务器的互联网连接数及流量；

`service serverSpeeder renewLic`  
：当有新的 License 文件可用时，联网更新 License 文件并重启锐速；

`service serverSpeeder update`  
：当有新的锐速版本可用时，联网更新锐速并重启锐速；
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExMjEwMDUzMDMsMTg0MTk0MzE3NCwxMj
E4NjIxMTAsMTEzOTQ3MTE1NSwxNjc3ODUxNjI4XX0=
-->
