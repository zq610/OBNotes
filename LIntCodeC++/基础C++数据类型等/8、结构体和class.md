## 1、结构体定义和使用
```cpp
//单独定义结构体
struct student{
	成员列表；
};
//创建结构体变量
struct student stu1;
student stu1 = {变量1，变量2....};
//定义+创建
struct studnet{
} stu1;
```
## 2、结构体数组
```C++
struct student arr[3] = {
	{"Jack", 18, 80},
	{"Suzi", 19, 60},
	{"Mike", 20, 70}
};
```
## 3、结构体指针
```c++
student stu1;
stu1.name;//1、结构体变量通过.访问成员
student *p = &stu1;//2、结构体指针p通过->访问成员
p->name;
```
## 4、结构体嵌套
## 5、结构体做函数参数
```c++
//1、值传递
void printStudent(student stu) {}
//2、引用传递
void printStudent(student& stu) {}
//3、地址传递
void printStudent(student* stu) {}
```