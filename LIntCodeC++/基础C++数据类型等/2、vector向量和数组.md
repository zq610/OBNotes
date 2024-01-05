**vector向量：高级数组，不需要提前声明容量。（像string一样自动开辟新内存）**
## 1、常用vector方法
| 方法 | 作用 |
| ---- | ---- |
| v.push_back(e) | 将元素存入vctor |
| v.begin() | 首地址 |
| v.end() | 尾地址（最后一个元素的后一位） |
| v.insert(ptr,e) | 在位置ptr插入e |
| v.erase(ptr1) | 删除ptr1指向的单个元素 |
| v.erase(ptr1,ptr2) | 删除ptr1，ptr2范围的元素 |
| v.size() | 返回vector中元素个数 |
| v.empty() |  |
| v.clear() |  |
| **sort(ptr1,ptr2)** | **排序** |
| **reverse(ptr1,ptr2)** | **反转** |

