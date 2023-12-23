inline

# 类中内联

## 1、类的成员函数默认为内联函数inline

## 2、显式定义inline函数

- 方式一：非类成员函数

```cpp
//(1)先声明函数
void Func(int n);
//(2)在定义函数体时加inline关键字
inline void Func(int n)
{
    cout<<n<<endl;
}
```

- 方式二：类成员函数
  
  ```cpp
  class A
  {
   public:
          //声明
         void Func(int x);
  }
  
  //类外定义
  inline void A::Func(int x)
  {
  
  }
  ```

## 3、编译器对inline函数的处理

1. 将inline函数体复制到调用处；

2. 为inline函数局部变量分配内存；

3. 为inline函数的输入参数和返回值映射到调用函数的局部变量空间中；

4. 当inline有多个返回值，转化为goto语句；

## 4、inline函数特点和用法

- inline函数是实现函数而非定义函数

- inline函数用代码膨胀(复制)换取性能，不适用于函数体开销大的函数

- inline函数每次调用都会复制，臃肿的代码会增加总代码量，消耗更多的内存

# 虚函数可以是内联函数吗

## 1、当虚函数表现多态性时不能内联inline

> 内联：在编译时内联
> 
> 虚函数多态：在运行时表现为多态性
> 
> 所以，当虚函数表现多态时，编译器无法知道应该调用哪个函数，无法内联
> 
>  

```cpp
class Base
{
 public:
    inline virtual void Print()
   {
        std::cout<<"I am Base!\n";
   }
    virtual ~Base(){}
};

class Derived: public Base
{
 public:
     inline void Print()
    {
        std::cout<<"I am Derived\n";
     }
};


int main()
{
    //虚函数print()通过指针调用，呈现多态性，运行时才能确定，不能内联
    Base *ptr = new Derived();
    ptr->Print();
}
```

## 2、编译器具有实际类对象，不是类的指针或调用时才能内联inline

```cpp
int main()
{
    //通过具体类对象b调用，编译时就确定函数，可以内联
    Base b;
    b.Print();
}
```
