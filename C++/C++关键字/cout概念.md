## cout
本身代表一个对象：默认是`ostream& os//不能加const`。
每次cout都改变cout对象的状态。

`extern _IO_ostream_withassign cout`
`class  _IO_ostream_withassign: public ostream`

## ostream
操作符<<重载了很多的对象
```c
...
ostream& operator<<(char)
ostream& operator<<(int)
ostream& operator<<(unsigned long)
ostream& operator<<(long)
.....

```

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTI3NTU4MTU4M119
-->
