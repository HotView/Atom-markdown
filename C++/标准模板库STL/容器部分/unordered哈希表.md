unorder就等于hash的意思
迭代器的类型取决于链表的类型：双向链表就是双向迭代器，单向链表就是单向迭代器。
## unordered_multiset
篮子：bucket
元素：elements
- 篮子里的元素是用链表的结构来存储的
- 篮子是映射查找，篮子里的元素是链表查找
- 篮子数应该大于元素数

方法
- bucket_count()
- load_factor()
- bucket_size()

自己有一个查找的方法find()
## unordered_multimap
单个篮子里的元素使用key/value来实现的
- insert插入的是一个pair元素
