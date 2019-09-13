## map的基本操作函数
map是一种关联式容器，包含“关键字/值”对
####属性
- size() 返回map中元素的个数
- empty() 如果map为空则返回true
#### 迭代器
- begin() 返回指向map头部的迭代器。
- end()指向最后一个元素。
#### 搜寻函数
- count（key）
- find（key）
- lower_bound(key)
- upper_bound(key)
- equal_bound(key)
#### 增加函数
- insert(elem) 插入元素
- insert(pos，elem) 插入元素
- insert(beg，end) 插入元素
#### 插入和移除
- erase(elem) 删除value与elem相等的所有元素
- erase(pos) 删除pos所指位置元素
- erase(beg，end) 删除区间元素
- clear()删除所有元素
