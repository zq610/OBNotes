## 1、定义与特点
存储相同数据类型元素的容器。
- 数据结构：红黑树的平衡二叉树
- 特点
	- 有序（默认升序）
	- 检索效率高于（vector、queue、list等容器）
	- 不可改，只可以增删查
	- 不可随机存取，使用迭代器访问元素
	- 元素不可重复，multiset多重集合容器可以
## 2、使用
### 1、声明
`set<T> s;`
`multiset<T> s;`
### 2、常用方法
| 方法 | 作用 |
| ---- | ---- |
| s.insert(e) | 插入元素e，默认升序排列 |
| s.erase(k) | 删除值为k的元素，返回删除元素数量0/1 |
| s.erase(ptr) | 删除迭代器ptr所指的元素 |
| s.find(k) | 查找值为k的元素，返回迭代器地址或s.end() |
### 3、操作和遍历
```cpp
set<int>::iterator ptr;
for(ptr = s.begin();s!=s.end();ptr++)
{
	cout<<*ptr<<endl;
}
```