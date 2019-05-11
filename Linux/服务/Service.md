1. 服务就是运行在操作系统后台的一个或多个程序，为用户或系统提供某项特定服务。
2. 服务通常是一直运行的，随时接受请求，不中断。
3. 我们日常用的最多的是网页服务，就是网站服务器上的http服务程序提供的。

- 基本操作
命令service可以用来调用指定服务的Sys V脚本，并执行动作
service 服务名 start
service 服务名 stop
service 服务名 restart
service 服务名 status
- 修改设置服务
chkconfig 服务名 【on/off】
chkconfig --list：列出所有的状态


> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTMwMTEyNDI1OSwxODQ5NDIxNDQzLC0xMz
E5OTg5NjQwXX0=
-->