# **C++ Priority Queue 容器**
## **基本概念**

`priority_queue` 是一种容器适配器，提供了元素按照优先级顺序进行存取的功能。默认情况下，`priority_queue` 是一个最大堆（max-heap），即优先级最高的元素位于队首。可以通过自定义比较函数来实现最小堆（min-heap）。

## **常用接口**
以下是 `priority_queue` 的一些常用接口：

```cpp
#include <queue>
#include <vector>
#include <functional>

// 默认是最大堆
std::priority_queue<int> pq;
std::priority_queue<int> pq2(pq); // 拷贝构造函数

// 最小堆的定义方式
std::priority_queue<int, std::vector<int>, std::greater<int>> minHeap;

// push()：在队尾添加元素
pq.push(10);

// pop()：移除队首元素
pq.pop();

// top()：访问队首元素
int top = pq.top();

// size()：返回队列中元素的数量
size_t size = pq.size();

// empty()：检查队列是否为空
bool isEmpty = pq.empty();
```

## **自定义比较函数**

可以通过自定义比较函数来改变 `priority_queue` 的排序方式。以下是一个自定义比较函数来创建一个最小堆的例子：

```cpp
#include <queue>
#include <vector>

struct myComparison {
    bool operator()(int lhs, int rhs) {
        return lhs > rhs; // 最小堆：lhs > rhs
    }
};

std::priority_queue<int, std::vector<int>, myComparison> customMinHeap;

// 添加元素
customMinHeap.push(10);
customMinHeap.push(20);
customMinHeap.push(5);

// 获取并移除队首元素
int top = customMinHeap.top(); // 5
customMinHeap.pop();
```
