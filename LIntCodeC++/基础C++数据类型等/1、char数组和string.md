# 1、本质
- char数组：末尾含‘\0’的数组(size=字符数+1)
- string：
# 2、函数比较
|  | **char[]** | **string** |
| ---- | ---- | ---- |
| **比较** | strcmp(c1,c2,n) | >=... |
| 拼接 | strcat(c1,c2,n);同时修改c1值 | + |
| 复制 | strcpy(c1,c2,n);修改并返回c1值 | = |
| 剪切 | strsub(char*);自定义 |  |
```cpp
char *strsub(char[] str1, char[] str2, int start, int end)
{
	int i = 0;
	for (int j = start; j < end; i++, j++) 
	{
     str1[i] = str2[j];
	}   
	str1[i] = 0;
	return str1;
}
```
## 3、string常用函数
| 方法(#include<string>) | 用途 |
| ---- | :--: |
| s.begin() | 返回s首地址 |
| s.end() | 返回s尾地址=最后字符的下一个位置 |
| s.insert(p,str) | 在位置p后插入str，返回s |
| s.insert(ptr,c) | 在迭代器ptr前面插入字符c |
| s.append(str) | 追加str到s末尾，返回s |
| s.erase() |  |
| s.rerplace(p,len,str) | 从p开始，用str替换长度len的字符 |
| s.compare(str) | 比较s和str |
| s.find(c/str) | 查找 |
| s.substr(p,len) | 获取子串 |
| s.length() |  |
| s.empty() |  |
| s.clear() |  |
| ==sort(ptr1,ptr2)== | ==迭代器范围字符按ASCII码顺序排序== |
| ==reverse(ptr1,ptr2)== | ==迭代器范围字符反转== |
需要`#include<algorithm>`
## 4、string分割字符串
```cpp
vector<string> SplitString(string& str1,string& t)
{
	vector<string> s;
	int start=0,pos;
	while(start<str1.size())
	{
		if(str1.find(t,start)==string::npos)
		{
			s.push_back(str1.substr(start));
			break;
		}
		pos = str1.find(t,start);
		s.push_back(str1.substr(start,pos-start));
		start = pos+t.size();
	}
	return move(s)
}
```