# 1、C中struct

- 只包含数据成员，无成员函数；

- 不能使用访问修饰符private、protected、public；

- 没有继承的概念；

- 结构体名字可以和函数名相同

- 结构体变量定义
  
  - struct Base base；
  
  - ```cpp
    typedef struct Base
    {
    }base;
    base b;//省略了struct
    ```

# 2、C++中struct

- 包含数据成员和成员函数

- 可使用访问修饰符

- 可继承

- 结构体名字可以和函数名相同，但定义结构体变量时要加struct区分

- 可以直接使用，不带struct(在没有同名函数的情况下)；

```cpp
struct A
{

}a;//a是一个结构体变量


typedef struct A
{

}a;//a是结构体类型
a a1;//a1才是变量
```

# 3、struct与class区别

## struct：默认public

## class：默认private
