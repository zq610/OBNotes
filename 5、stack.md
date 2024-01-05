## 1、定义
**先进后出的数据结构**
## 2、常用方法
| 方法 | 作用 |
| ---- | ---- |
| s.push(e) |  |
| s.pop() |  |
| s.empty() | 判空 |
| s.top() | 读取栈顶元素 |
## 3、判断出栈序列是否合法
```cpp
bool Train(vector<int>& in_order,vector<int>& leave_order)
{
	stcak<int> trian;
	int leave = 0;
	for(int order:in_order)
	{
		if(order == leave_order[leave])
		{
			leave++;
			while(train.empty()!=0)
			{
				if(train.top==leave_order[leave])
				{
					train.pop();
					leave++;
				}else
				{
					break;
				}
			}
		}else
		{
			trian.push(order);
		}
	}
	return train.empty();
}
```