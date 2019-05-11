==没有名字的函数==
anonymous function
冒号前面是**输入**，冒号后面的表达式是**输出**。
示例1
```
def f(x):
	return 3*x +1

lambda x: 3*x+1

g = lambda x:3*x+1

```
示例2
```python
full_name  = lambda fn,ln:fn.strip().title()+""+ln.strip().titile()
```
示例3
```python
//冒号后面是返回值。
lambda :
lambda x:
lambda x,y:
lambda x,y,z:
lambda x1,x2,x3,...,xn:
```
示例3
```python 
def build_quadratic_function(a,b,c):
	return lambda x:a*x**2+b*x+c
```
## 二、 lambda表达式在sort中的使用
sort基本用法
sort()函数用来对list数据类型进行排序。reverse为True时，从大到小进行排序；默认为False，从小到大进行排序。
sort函数在原list进行排序，sorted函数返回一个新的list
`list.sort(key=..., reverse=...)#sort函数在原list进行排序`
`sorted(list, key=..., reverse=...)#sorted函数返回一个新的list`
#### key可以为一个函数
- 此时传入key函数的参数为待排序的类型中的一个元素。
- lambda表达式中的输入是待排序类型的一个元素，输出的是元素的属性。按照输出的元素的某个属性为条件进行排序。
```python
# take second element for sort
def takeSecond(elem):
    return elem[1]

random list
random = [(2, 2), (3, 4), (4, 1), (1, 3)]

# sort list with key
random.sort(key=takeSecond)

# print list
print('Sorted list:', random)


# output
Sorted list: [(4, 1), (2, 2), (1, 3), (3, 4)]

```
### 使用lambda表达式
```python
a = [(1, 2), (4, 1), (9, 10), (13, -3)]
a.sort(key=lambda x: x[1])

print(a)
# Output: [(13, -3), (4, 1), (1, 2), (9, 10)]
```

这里传入lambda表达式形参x的实参为列表a中的每一个元素

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTk1MDY2OTQyNiwtMTM4NzYxNDE1NSwyMD
QzMzQ0NjksLTEzNzQ2NjY0MTBdfQ==
-->