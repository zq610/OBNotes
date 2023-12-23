# 1、C++/C编译区别

- C：编译器编译

- C++：兼容C，但因为有新特性，例如函数重载，编译后的文件会包含函数的参数类型(C没有)。从而导致在C++中使用C函数会出现编译链接错误

> extern  “C” 修饰的函数（头文件中），在链接时会取找寻c类型的符号，而不是C++类型的

# 2、C++调用C函数

C++可以直接调用编译好的C函数。

```cpp
//法一：
//add.h
#ifdef ADD_H
#define  ADD_H
extern int add(int x,int y);
//add.cpp
extern "C"{
    #include "add.h"
}
//法二:Cpp文件不用extern “C”了
//add.h  
#ifdef _cplusplus
extern "C"{
#endif
 int add(int x,int y);  
#ifdef _cplusplus
}
#endif
```

# 3、C中调用C++

将C++代码重新当c编译后使用，并非直接调用。

```cpp
//因为c不支持extern “c”，所以放在cpp文件或头文件中
//add.h
#ifdef ADD_H
#define  ADD_H
extern "C"{
    int add(int x,int y);  
}
//add.c
extern int add(int x,int y);
```
