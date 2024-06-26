# 操作符

## #字符串化操作符

预处理器会将#后面的参数转化为字符数组（字符串）

- 只能用于有传入参数的宏定义

- #必须置于宏定义体内的参数名前

- 空格处理规则：忽略传入参数前面和后面的空格，子字符串中间用一个空格连接。
  
  ```cpp
  #define exp(s) #s
  string str = exp(  bac);//bac
  string str1 = exp(  abc  dfg);// abc dfg
  ```

## ##符号连接操作符

先分隔，再强制链接。将宏定义的多个形参转换成一个实际参数名

- 用##连接形参，##前后的空格可有可无

- 连接后的实际参数名，必须为实际存在的参数名/编译器已知的宏定义

- ##后的参数本身也是宏，##会阻止这个宏展开
  
  ```cpp
  //##前后空格可有可无
  #define expA(s) printf("前缀加上后的字符串为：%s\n",gc_   ##  s)
  //gc_s必须存在
  #define expA(s) printf("前缀加上后的字符串为：%s\n",gc_   ##  s)
  ```

## \续行工作符

# do{} while（0）的使用

## 1、避免语义曲解

```cpp
//添加{}，虽然避免了歧义，但末尾多了一个；
#define fun() {fun1();fun2()}
if(a>0)
   fun();
//宏展开
if(a>0)
{
    fun1();
    fun2();
};
//用do while(0)宏定义可避免
#define fun() \
   do{ \
      fun1();\
      fun2();\
    }while(0)\
//while(0)保证逻辑只执行一次
```

> 使用do{}while(0)包裹逻辑可以使得无论如何加括号分号，逻辑都可以正常运行

## 2、避免使用goto控制流

使用do{}while(0)中添加break语句，避免使用goto

## 3、避免由宏引起的警告

#define EMPTYMICRO  d0{}while(0) 

用来定义空宏，避免警告

## 4、定义单一函数快完成复杂操作

即使用do{}while(0)来缩小作用域，在域内可任意使用变量，不用考虑同名冲突等；
