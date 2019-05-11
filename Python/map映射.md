
map()会根据提供的函数对指定的序列做映射。
第一个参数function以参数序列中的每一个元素调用function函数，返回包含每次function函数返回值的新列表。
## 语法
`map(function,iterable,....)`
## 实例
```python
def square(x):
	return x**2
map(square,[1,2,3,4,5])
```
```py
map(lambda x:x**2,[1,2,3,4,5])
```

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTM2OTY5ODEyXX0=
-->