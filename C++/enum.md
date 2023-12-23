# 传统enum问题

- 作用域不受限，容易引起命名冲突
  
  解决：（1）使用前缀区分不同enum的变量
  
             （2）命名空间限制作用域
  
             （3）类或者结构体限制作用域（最有效）

- 会隐式转换为int

- 用来表征枚举变量的实际类型不能明确，从而无法支持枚举类型前向声明(只能声明同时初始化)

# C++11枚举类

enum class 可以很好地解决上述问题

- 作用域不再是全局

- 不能隐式转换为其他类型
  
  ```cpp
  enum class color
  {
      RED = 2;
      YELLOW;
      BLUE;
  }
  color c = color::YELLOW;
  cout<<static_cast<int>(c)<<endl;//必须通过强制转换显示转换
  ```
  
  

- 可以指定用特定的类型来存储enum
  
  ```cpp
  enum class color:char;//支持前向声明，char类型数据
  
  enum class color:char
  {
      red = 'r';
      blue;
  }
  char c = static_cast<char>(color::red);
  ```

# 类中的枚举类型

可用枚举类型建立在整个类中都恒定的常量（const成员只能控制同一个类对象作用域不变）

```cpp
class Person
{
 public:
    typedef enum{
       BOY  =  0;
       GIRL
    }SexType;
}
//访问
Person::BOY
```

- 枚举常量不占用对象的存储空间，在编译时被全部求值

- 隐含数据类型为整数，范围有限，不支持浮点 
