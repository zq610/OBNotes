# Lambda表达式

## 1、基础

Lambda表达式提供了类似于匿名函数（用于需要一个函数，但又不必要去特别命名）的特性

```cpp
[捕获列表](参数列表)mutable(可选) 异常属性->返回类型
{
    
}
```

## 2、捕获列表

用于捕获外部数据传递给函数体使用，可以理解为参数的一种类型

### 1、值捕获

相当于参数传值。

前提：变量允许拷贝

不同：捕获的变量在lambda表达式创建时拷贝，非调用时；

```cpp
int value = 1;
auto copy_value = [value]{
    return value;
};

int value=100;
cout<<copy_value()<<endl;//输出1，非100；
```

### 2、引用捕获

相当于引用传参

```cpp
int value = 1;
auto copy_value = [&value]{
    return value
};

value = 10;
cout<<copy_value()<<endl;//输出10，是value的实时值

```

### 3、隐式捕获

让编译器自动推导捕获列表

[=]:值捕获

[&]:引用捕获

### 4、表达式捕获

值捕获、引用捕获、隐式捕获：全是捕获的在外部已经声明的变量，捕获的左值；

表达式捕获（C++14）：允许捕获成员用任意的表达式进行初始化，允许右值捕获

```cpp
auto Important = make_unique<int>(1);
auto add = [v1=1,v2 = move(important)](int x,int y)->int{
    return x+y=v1=(*v2);
}
//important是一个独占指针，不能被捕获，用move转化为右值，在表达式中初始化
```

## 3、泛型Lambda

auto关键字不能用于参数表，会与模板功能冲突

Lambda表达式中可以使用auto产生泛型（C++14）

```cpp
auto add = [](auto x,auto y)
{
    return x+y;
}
```


