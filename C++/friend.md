# 概述

友元允许普通函数或类成员函数访问另一个类的私有成员。

1. 友元函数：可以访问类的私有/保护成员

2. 友元类：类A的成员函数可以访问类B中的私有/保护成员
   
   优：提高程序运行效率
   
   缺：破环类的封装性和数据透明性

特点：

- 友元关系不可传递

- 友元关系的单向性

- 友元关系的不可继承性

- 友元声明的形式和数量无限制

# 友元函数

友元函数的声明在任何地方，定义必须在类的外部。

```cpp
class Apple
{
private:
	string m_Name;
public:
	Apple(string name)
		:m_Name(name) {};
    //友元声明
	friend string GetName(Apple& apple);
};
//友元函数定义
string GetName(Apple& apple)
{
	return apple.m_Name;
}

int main()
{
	Apple apple = Apple("RedApple");
    //友元函数调用
	GetName(apple);
}
```

# 友元类

友元类声明在类的声明中，实现在类外

```cpp
class Apple
{
private:
	string m_Name;
public:
	Apple(string name)
		:m_Name(name) {};
     //友元类声明
	friend class Pear;
};

class Pear
{
public:
	string GetName(Apple& apple)
	{
		return apple.m_Name;
	}
};


int main()
{
	Apple apple = Apple("RedApple");
	Pear pear;
	pear.GetName(apple);
}
```


