## 1、定义
元素以键值对的形式存储的数据结构
`map<T,T> m;`
`multimap<T,T> m;`
## 2、常用方法
### 1、操作
| 方法 | 作用 |
| ---- | ---- |
| m.insert(pair<T,T>(k,v)) | 插入新元素，默认键值升序 |
| m.erase(k) | 删除所有键为k的元素，返回删除总数 |
| m.find(k) | 查找第一个键为k的元素迭代器位置 |
### 2、遍历
```cpp
//1、遍历
map<T,T>::iterator it;
for(it=m.begin();it!=m.end();it++)
{
cout<<(*it).first<<it->second<<endl;
}
//2、访问或者新建元素
m[k] = v;//仅限map类型，multimap多重映射容器不行
m.insert(pair<T,T>(k,v));//均可
//3、查找元素
if(m.find(k)==m.end())
{
	//元素不存在
}else
{
	//元素存在，并返回迭代器地址
}

```