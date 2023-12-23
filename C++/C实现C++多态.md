# C++实现多态

## 1、多态

在C++中会维护一张虚函数表，当调用成员函数时，会根据调用函数的对象的类型来执行不同的函数。

即根据指针或者引用指向对象的类型，而不是该指针和引用本身的类型，调用对应的虚函数。

## 2、C++实现

```cpp
Base *base = new Derived();
base->func();//调用派生类同名函数
Base base;
Base *ptr =&base;
ptr->func();//调用基类自己的函数 
```

# C实现多态

采用结构体struct实现

```cpp
//定义一个函数指针类型
typedef void(*pf)();
//父类
typedef struct _A
{
    pf _f;
}A;
//派生类
typedef struct _B
{
    A _b;//通过结构体的嵌套实现继承
}B;


A a;
B b;
a._f = FuncA;
b._b._f = FuncB;
A *pa = &a;
pa->_f();//FuncA()

pa = (A *)&b;
pa->_f();//FuncB()
```
