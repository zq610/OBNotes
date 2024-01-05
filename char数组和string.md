# 1、本质
- char数组：末尾含‘\0’的数组(size=字符数+1)
- string：
# 2、函数比较
|  | **char[]** | **string** |
| ---- | ---- | ---- |
| **比较** | strcmp(c1,c2,n) | >=... |
| 拼接 | strcat(c1,c2,n);同时修改c1值 | + |
| 复制 | strcpy(c1,c2,n);修改并返回c1值 | = |
| 剪切 | strsub(char*);自定义 |  |
```cpp
char *strsub(char[] str1, char[] str2, int start, int end)
{
	int i = 0;
	for (int j = start; j < end; i++, j++) 
	{
     str1[i] = str2[j];
	}   
	str1[i] = 0;
	return str1;
}
