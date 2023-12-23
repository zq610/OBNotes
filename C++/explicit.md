# 修饰构造函数

防止隐式转换和复制初始化，必须显示的调用构造函数

```cpp
explicit Entity(int num)
    :m_num(num)
{
    
}
Entity e = 22;//error explicit禁用隐式转换
Entit e = Entity(22);//必须显示调用构造构造函数
```



# 修饰转换函数（operator重载，显示转换函数）

防止隐式转换（按语境转换除外）：即只能显示的调用转换函数进行转换。

在if()条件语句中可以允许语境转换
