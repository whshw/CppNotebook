# C++ stack容器

## 基本概念

`stack`是一种容器适配器，它给予程序员了LIFO（后进先出）数据结构的功能。在`stack`中，元素只能从顶部添加和移除，也就是说，`stack`只允许在其顶部进行插入和删除操作。

## 常用接口

以下是`stack`的一些常用接口：

```cpp
#include <stack>

std::stack<int> s;
std::stack<int> s2(s); // 拷贝构造函数

// push()：在栈顶添加元素
s.push(10);

// pop()：移除栈顶元素
s.pop();

// top()：访问栈顶元素
int top = s.top();

// size()：返回栈中元素的数量
size_t size = s.size();

// empty()：检查栈是否为空
bool isEmpty = s.empty();
```