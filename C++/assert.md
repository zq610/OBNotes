# 用途

1、assert是宏，如果它的条件不满足，就终止程序运行。

2、常用于检查逻辑上不可能的情况：

    1、在运行前和运行后检查状态

    2、在运行期间被禁用 在头文件include之前加上`#define NDEBUG`禁用断言

3、头文件

```cpp
#include<assert.h> //C
#include<cassert>//C++

int main()
{
    int x = 10;
    assert(x==7);//当x！=7时，退出程序
    return 0;
}
```
