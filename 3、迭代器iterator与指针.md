**用来遍历一个容器的工具**
## 1、使用方式
- 定义
	`vector<int>::iterator p;`
- 使用
	`for(p=v.begin();p!=v.end();p++)`
		`cout<<*p<<endl;`
	与指针类似，可以用`*p`来访问迭代器指向地址的内容