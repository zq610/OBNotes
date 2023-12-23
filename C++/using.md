# 全局与局部使用using

```cpp
using namespace std;//命名空间
using std::string;//std命名空间中的string
using ::func;//使用全局中的函数
using ns::func;//使用局部的func函数
```

# 改变访问性

```cpp
class A
{
 public:
     size_t Size() const;
 protected:
     size_t n;
}

class B : private A
{
 public: 
      using Base::Size;//本来私有继承应该是私有的，但using语句，使得size()可以按public访问   
}
```

# 函数重载

```cpp
```cpp
class A
{
 public:
     void func();
     void func(int n);
};

class B:private A
{
 public:
     using A::func;//将A的所有重载实例添加到派生类B的作用域中
     void func(int n)//特有的函数单独定义，其他继承而来的函数不用重新定义
     {
         cout<<"B::func"<<endl;
     }
}
```



# typedef

typedef A B ；

using B=A;
