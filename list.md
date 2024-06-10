# C++ list容器

## 基本概念

`list`是一种序列容器，它允许快速的插入和删除操作。与`vector`和`deque`不同，`list`的元素在内存中不是连续存储的，因此它不支持直接访问元素。

## 构造

```cpp
#include <list>

std::list<int> list1; // 创建一个空的list
std::list<int> list2(5, 10); // 创建一个包含5个元素的list，每个元素的值都是10
std::list<int> list3(list2.begin(), list2.end()); // 使用另一个list的迭代器来构造新的list
std::list<int> list4(list3); // 使用另一个list来复制构造新的list
```

## 赋值和交换

1. `list` 容器支持赋值操作，可以使用`=`运算符将一个`list`赋值给另一个`list`
2. `list` 容器还提供了`assign(n, elem)` 和 `assign(first, last)` 函数来进行赋值操作
3. `list` 容器还支持 `swap()` 函数，可以交换两个`list`的内容

```cpp
std::list<int> list1(5, 10);
std::list<int> list2;

list2 = list1; // 将list1的内容赋值给list2
list2.assign(list1.begin(), list1.end()); // 将list2赋值为list1的内容
list1.assign(5, 20); // 将list1赋值为5个值为20的元素

list1.swap(list2); // 交换list1和list2的内容
```

## 大小操作

`list`容器提供 `size()` 和 `empty()` 函数来获取容器的大小和检查容器是否为空，还提供 `resize()` 函数来改变容器的大小

```cpp
size_t size = list1.size(); // 返回list中元素的数量
bool isEmpty = list1.empty(); // 检查list是否为空
list1.resize(10); // 改变list的大小为10
list1.resize(10, 20); // 改变list的大小，并用20填充新元素
```

## 插入和删除

```cpp
list1.push_back(30); // 在list的末尾添加一个元素
list1.push_front(20); // 在list的开始添加一个元素
list1.pop_back(); // 删除list的最后一个元素
list1.pop_front(); // 删除list的第一个元素
list1.insert(list1.begin(), 40); // 在list的第一个位置插入一个元素
list1.insert(list1.begin(), 3, 50); // 在list的第一个位置插入3个元素
list1.insert(list1.begin(), list2.begin(), list2.end()); // 在list的第一个位置插入另一个list的元素
list1.erase(list1.begin()); // 删除list的第一个元素
list1.erase(list1.begin(), list1.begin() + 3); // 删除list的前3个元素
list1.clear(); // 删除list中的所有元素
list1.remove(10); // 删除list中所有值为10的元素
```

## 数据存取

```cpp
int front = list1.front(); // 访问list的第一个元素
int back = list1.back(); // 访问list的最后一个元素
```

## 反转和排序

```cpp
list1.reverse(); // 反转list中的元素
list1.sort(); // 对list中的元素进行排序
```

以上就是C++中`list`容器的基本概念，构造，赋值和交换，大小操作，插入和删除，数据存取，反转和排序的介绍。