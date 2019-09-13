new分解为三个动作：
- 调用operator new
- 指针转换
- 初始化

## 重载operator new
- 可以全局重载operator new，这个影响很广泛，对所有的类都会有影响。
- 也可以对某个类重载operator new

如果使用者绕过某个你重载的设计，语法上提供这个功能：`Foo*=::new Foo；`强制采用全局的函数。
## placement new
operator new可以重载多个不同的形式，但是参数列表必须不同，然后new表达式时参数列表形式与其相似即可（即除了默认参数之外的参数都会放在new表达式的圆括号中），这样的new就被称为placement new

==当然也可以重载class operator delete，但不会被调用，只有对应版本的new抛出异常，才会被调用。==
