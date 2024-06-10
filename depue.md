## 基本概念

`deque`（双端队列）是一种具有动态大小的序列容器，它可以在其两端进行元素的插入和删除操作。`deque`容器在内存中并不保证所有元素的连续性，因此它不支持像`vector`和`array`那样的直接内存访问操作。

## 构造

在C++中，我们可以使用多种方式来构造`deque`：

```cpp
#include <deque>

std::deque<int> deque1; // 创建一个空的deque
std::deque<int> deque2(5, 10); // 创建一个包含5个元素的deque，每个元素的值都是10
std::deque<int> deque3(deque2.begin(), deque2.end()); // 使用另一个deque的迭代器来构造新的deque
std::deque<int> deque4(deque3); // 使用另一个deque来复制构造新的deque
```

## 赋值操作

`deque`容器支持赋值操作，可以使用`=`运算符将一个`deque`赋值给另一个`deque`：

```cpp
std::deque<int> deque1(5, 10);
std::deque<int> deque2;

deque2 = deque1; // 将deque1的内容赋值给deque2
```

此外，`deque`还提供了`assign()`函数来进行赋值操作：

```cpp
std::deque<int> deque1;
deque1.assign(5, 10); // 将deque1赋值为5个值为10的元素
```

以上就是C++中`deque`容器的基本概念，构造和赋值操作的介绍。