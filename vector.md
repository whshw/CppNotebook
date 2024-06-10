# C++ vector容器

## 基本概念

`vector`是C++标准库中的一种序列容器，它可以容纳可变数量的元素，并且能够动态地调整其大小。

## 构造函数

```cpp
#include <vector>

std::vector<int> vec1; // 创建一个空的vector
std::vector<int> vec2(5, 10); // 创建一个包含5个元素的vector，每个元素的值都是10
std::vector<int> vec3(vec2.begin(), vec2.end()); // 使用另一个vector的迭代器来构造新的vector
std::vector<int> vec4(vec3); // 使用另一个vector来复制构造新的vector
```

## 赋值

```cpp
vec1 = vec2; // 将vec2的内容赋值给vec1
vec1.assign(5, 20); // 将vec1赋值为5个值为20的元素
vec1.assign(vec2.begin(), vec2.end()); // 将vec1赋值为vec2的内容
```

## 容量和大小

```cpp
size_t size = vec1.size(); // 返回vector中元素的数量
size_t capacity = vec1.capacity(); // 返回vector的容量
bool isEmpty = vec1.empty(); // 检查vector是否为空
vec1.resize(10); // 改变vector的大小
vec1.resize(10, 20); // 改变vector的大小，并用20填充新元素
```

## 插入和删除

```cpp
vec1.push_back(30); // 在vector的末尾添加一个元素
vec1.pop_back(); // 删除vector的最后一个元素
vec1.insert(vec1.begin(), 20); // 在vector的开始插入一个元素
vec1.insert(vec1.begin(), 3, 50); // 在vector的开始插入3个元素
vec1.erase(vec1.begin()); // 删除vector的第一个元素
vec1.erase(vec1.begin(), vec1.begin() + 3); // 删除vector的前3个元素
vec1.clear(); // 删除vector中的所有元素
```

## 数据存取

```cpp
int first = vec1.front(); // 访问vector的第一个元素
int last = vec1.back(); // 访问vector的最后一个元素
int element = vec1[0]; // 使用下标访问vector的元素
int element2 = vec1.at(1); // 使用at()函数访问vector的元素
```

## 互换容器

```cpp
vec1.swap(vec2); // 交换vec1和vec2的内容
```

## 预留空间

```cpp
vec1.reserve(100); // 预留100个元素的空间
```