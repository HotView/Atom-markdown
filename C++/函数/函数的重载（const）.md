我们常常需要用两个或多个函数完成相同的任务，但其参数的类型不同。

函数重载允许一个程序中的若干函数使用相同的名称，只要他们的参数列表不同即可。

==符号修饰或符号改编==

## 重载和指针参数
指向不同类型的指针是不同的，因此下面的原型声明了不同的重载函数
```c
int largest(int* pValue,size_t count);
ing largest(float* pValue,size_t count);
```
## 重载和引用参数
如果重载带有引用参数的函数，就需要小心。
不能把参数是类型data_type的函数，重载为参数类型是data_type&的函数。

## 重载和const参数
const参数与非const参数的唯一区别是==为引用定义参数==，还是为指针定义参数。
- 重载和const指针参数
一个函数的参数类型是type*，而另一个是const type*，这两个函数就是不同的。以下函数有不同的函数签名
`long *largee(long* a,long* b);`
`const long *largee(const long* a,const long* b);`
- 重载和const引用参数
引用参数在声明为const时更为简单，类型T&和const T&总是不同的，所以，类型const int&和int &不同。
`long &larger(long& a,long &b);`
`long &larger(const long& a,const long &b);`
第一个函数不接受常量作为变元。
第二个函数接收常量和非常量的参数作为变元。

## const
const修饰函数参数
- 传递过来的参数在函数内不可以改变(无意义，因为Var本身就是形参)
void function(const int Var);

- 参数指针所指内容为常量不可变
void function(const char* Var);

- 参数指针本身为常量不可变(也无意义，因为char* Var也是形参)
void function(char* const Var);

- 参数为引用，为了增加效率同时防止修改。修饰引用参数时：
void function(const Class& Var); //引用参数在函数内不可以改变
void function(const TYPE& Var); //引用参数在函数内为常量不可变
## C，C++的const
#### C语言中的`const`:

-   `const`修饰的变量是只读的，本质还是变量
-   `const`修饰的局部变量在栈上分配空间
-   `const`修饰的全局变量在只读存储区分配空间
-   `const`只在编译期有用，在运行期无效
-   `const`不能定义真正意义上的常量

==`const`修饰的变量不是真的常量，它只是告诉编译器该变量不能出现在赋值符号的左边。==`const` 局部变量是在栈上分配空间，可以通过指针改变这个空间里面的值。过了编译期，`const`变量的常量特性，只读特性就没有了，只读特性只在编译期有效，运行期根本无效。`const`修饰的全局变量在只读存储区分配空间，因此如果用指针去修改了`const`修饰的全局变量，程序就会崩溃，因为修改了程序只读存储区中内容，大部分程序都会发生崩溃。

#### 2、C++中的`const`：

 C++在C的基础上对`const`进行了进化处理，具体表现在：

-   `const`声明时，在符号表中放入常量
-   编译过程中发现常量直接以符号表中的值替换（常量折叠）
-   编译过程中也可能为对应的常量分配存储空间：
    
    -   `const`用在全局或者使用了`static`关键字说明，存放在只读数据区
        
        ```
        extern const int i = 10;
        static const int i = 10;
        
        // 或者修饰全局变量
        const int a =10;
        int main()
        {}
        ```
        
    -   局部变量中对`const`常量使用了`&`操作符，在栈区分配空间

> 注意：C++编译器虽然可能为`const`常量分配空间，但不会使用其存储空间中的值
> 
> 符号表是编译过程中产生的一种数据结构
> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTM3NzYzNjM5LDE3NzM2NjY4MDIsNTk1ND
IxMDgsMTQ1MzQzMzQ2MF19
-->