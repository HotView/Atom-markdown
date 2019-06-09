const主要是解决reference中，为了不改变原变量的值，而设计出的一种性能，使得参数传递中不用拷贝传递，节省大量时间，又防止了对于原变量的修改，使得原变量只能被读取！
## const关键字的变量
常类型是指使用类型修饰符const说明明的类型，常类型的变量或者对象的值是不能被更新的。不管出现在任何上下文都是为了这个目的而服务的。
## const参数
const参数与非const参数的唯一区别是为（引用定义参数），还是为指针定义参数。
对于基本类型const int与int是相同的结果。
1. const指针参数
2. const引用参数
`void function(const Class& Var)`//引用参数在函数内不可改变
`void function(const TYPE& Var)`//
	>这样的一个const引用传递和最普通的函数按值传递的效果是一模一样的,他禁止对引用的对象的一切修改,唯一不同的是按值传递会先建立一个类对象的副本, 然后传递过去,而它直接传递地址,所以这种传递比按值传递更有效.==优点：速度更快。==
	>>另外==只有引用的const传递可以传递一个临时对象==,因为==临时对象都是const属性==, 且是不可见的,他短时间存在一个局部域中,所以==不能使用指针==,只有引用的const传递能够捕捉到这个家伙.
## const对象和const函数成员
#### const对象
> 在一个类中，任何不会修改数据成员的函数都应该声明为const类型。如果在编写const成员函数时，不慎修改了数据成员，或者调用了其它非const成员函数，编译器将指出错误，这无疑会提高程序的健壮性。

将一个对象声明为const，例如：`const Box box1；`。Box是一个类，编译器不允许给const对象调用volume函数成员，因为这可能修改对象，所以你需要告诉编译器volume函数不会修改对象。
方法是：
- 在类定义中把函数指定为const
```c++
class Box
{
	double volume() const;//
};
```
- 以相同的方式修改函数定义
```c
double Box::volume()const
{
	return length*width*height;
}
```
#### cons函数成员
把函数成员声明为const，会影响函数的签名。也就是说，可以通过添加函数的const版本来重载函数。
const对象的数据成员一般不能被修改。如果人们希望修改const对象的类成员，为此，可以把这种成员指定为mutable例如
```c
class Box
{
	private:
		double length;
		double width;
		double height;
		mutable std::string name;
		//....
}
```


## const难点
-  如果函数需要传入一个指针，面试官可能会问是否需要为该指针加上const，把const加在指针不同的位置有什么区别；如果写的函数需要传入的参数是一个复杂类型的实例，面试官可能会问传入值参数或者引用参数有什么区别，什么时候需要为传入的引用参数加上const。 const是用来声明一个常量的，当你不想让一个值被改变时就用const，const int max和int const max 是没有区别的，都可以。不涉及到指针const很好理解。一旦涉及到指针，则比较容易出问题。
![enter image description here](https://images0.cnblogs.com/blog/460416/201310/06213516-4b1d0d0e98694530b7e588d5e980a3dc.png)
-  如果const ==位于星号的左侧==，则const就是用来修饰指针所指向的变量，即指针指向的对象为常量；不能通过指针指向的方式修改对象的值，不能==修改对象的值，但是可以修改指针的值==。
- 如果const ==位于星号的右侧== ，const就是修饰指针本身，即指针本身是常量。 这是可以通过指针指向的方式来修改对象的值，但是==不能对指针本身进行修改==。
-  因此，[1]和[2]的情况相同，都是指针所指向的内容为常量（const放在变量声明符的位置无关），这种情况下不允许对内容进行更改操作，如不能*a = 3 ；[3]为指针本身是常量，而指针所指向的内容不是常量，这种情况下不能对指针本身进行更改操作，如a++是错误的；[4]为指针本身和指向的内容均为常量。
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbNTc5Mzc0Nzk2XX0=
-->
