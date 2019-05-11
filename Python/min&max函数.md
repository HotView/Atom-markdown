## min函数
与max函数类似，也是将对象（一般都是迭代器）进行操作，一般是len函数。
## max函数
```py
def max(*args, key=None):  # known special case of max  """ 
	max(iterable, *[, default=obj, key=func]) -> value 
	max(arg1, arg2, *args, *[, key=func]) -> value With a single iterable argument, return its biggest item. 
	The default keyword-only argument specifies an object to return if the provided iterable is empty. 
	With two or more arguments, return the largest argument. """  pass
```
输入两个对象，然后用key对应函数进行操作，最后得出结果，对结果值进行比大小，取最大值和最小值。
## argmin
返回最小值的索引
## argmax
返回最大值的索引
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTM0MDIwODY5NSwyMDQwMjU0OTQ1XX0=
-->