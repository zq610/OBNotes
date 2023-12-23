# 1、基本用法

decltype（expression）用于查询表达式类型（不会计算）

## （1）推导表达式类型

## （2）与using/typedef合用，用于定义类型，实现和auto类似的功能

```cpp
using size_t = decltype(sizeof(0));
using nullptr_t = decltype(nullptr);
typedef decltype(vec.begin()) vectype;(3)
```

## (3)重用匿名类型

```cpp
struct
{

}S;
decltype(S) as;//定义一个匿名类型的结构体
```

## （4）泛型编程结合auto，用于追踪函数返回值类型（最大用途）

```cpp
template<typename T>
auto multiply(T x,T y)->decltype(x*y)
{
    return x*y;
}
```

# 2、判别规则

```cpp
//规则一：推导为其类型（重载函数会编译错误）
//规则二：将亡值。推导为类型的右值引用
//规则三：左值。推导为类型的引用
//规则四:都不是，推导为本类型
```
