# C++ queue容器

## 基本概念

`queue`是一种容器适配器，它给予程序员了FIFO（先进先出）数据结构的功能。在`queue`中，元素只能从后端（称为队尾）添加，并从前端（称为队首）移除。

## 常用接口

以下是`queue`的一些常用接口：

```cpp
#include <queue>

std::queue<int> q;
std::queue<int> q2(q); // 拷贝构造函数

// push()：在队尾添加元素
q.push(10);

// pop()：移除队首元素
q.pop();

// front()：访问队首元素
int front = q.front();

// back()：访问队尾元素
int back = q.back();

// size()：返回队列中元素的数量
size_t size = q.size();

// empty()：检查队列是否为空
bool isEmpty = q.empty();
```