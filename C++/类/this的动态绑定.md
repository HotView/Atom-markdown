## 应用框架和应用之间的关系
应用框架里面有一些函数不知道怎么写，需要另外一部分开发人员来定义。则就可以声明为虚函数，然后另外一部分人实现之后，就可以在动态的调用那个开发人员定义的虚函数。
Application Framework
```c
CDocument::OnFileOpen()
{
	,,,,
	Serialize();
	....
}
virtual Serialize();
```
Application
```c
class CMyDoc:public CDocument
{
	virtual Serialize(){....}
}
```
使用
```c
main()
{
	CMyDoc myDoc;
	...
	myDoc.OnFileOpen();
}
```
在上述的说明中，成员函数的调用就默认传递一个this指针，即成员函数的调用者。
`CDocument::OnFileOpen( &myDoc )`，在框架里执行到Serialize()转换为this->Serialize( )，编译器检验是否满足动态绑定的要求，检查之后满足，翻译为`(*(this->vptr)[n] ) ( this )`进行动态绑定。
