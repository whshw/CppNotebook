# C++ set容器

## 基本概念

`set`是一种关联容器，它包含的元素按一定的顺序排列。每个元素在`set`中只出现一次，因为`set`的键即是值，也就是说，键和值是相同的。底层结构是用红黑树实现。

## 构造和赋值

```cpp
#include <set>

std::set<int> set1; // 创建一个空的set
std::set<int> set2(set1.begin(), set1.end()); // 使用另一个set的迭代器来构造新的set
std::set<int> set3(set2); // 使用另一个set来复制构造新的set

set1 = set2; // 将set2的内容赋值给set1
```

## 大小和交换

```cpp
size_t size = set1.size(); // 返回set中元素的数量
bool isEmpty = set1.empty(); // 检查set是否为空

set1.swap(set2); // 交换set1和set2的内容
```

## 插入和删除

```cpp
set1.insert(10); // 在set中插入一个元素
set1.erase(10); // 从set中删除一个元素
set1.erase(set1.begin()); // 删除set的第一个元素
set1.erase(set1.begin(), set1.end()); // 删除set的所有元素
set1.clear(); // 删除set中的所有元素
```

## 查找和统计

```cpp
std::set<int>::iterator it = set1.find(10); // 查找值为10的元素
size_t count = set1.count(10); // 统计值为10的元素的数量
```

## set和multiset的区别

+ `set` 不可以包含重复的元素，而 `multiset` 可以包含重复的元素。
+ `set` 插入数据的同时会返回一个 `pair<iterator, bool>` 类型的值，其中 `iterator` 指向插入的元素，`bool` 表示是否插入成功；而 `multiset` 插入数据的同时只会返回一个 `iterator` 类型的值，指向插入的元素。因此，`multiset` 可以插入重复的元素，而 `set` 不可以。

## pair类型

`pair` 是成对出现的数据结构，它包含两个数据成员，分别为 `first` 和 `second`。`pair` 可以用来存储两个数据的组合。

## 构建pair

```cpp
#include <utility>
pair<int, string> p1(1, "one");
pair<int, string> p2 = make_pair(2, "two");
```

## `set` 容器排序

`set` 容器默认是按升序排序的，如果想要改变排序方式，可以使用自定义的比较函数。

```cpp
#include <set>
#include <functional>

std::set<int, std::greater<int>> set1; // 降序排序
```

也可以使用 lambda 表达式来自定义比较函数：

```cpp
std::set<int, decltype([](int a, int b) { return a > b; })> set1;
```