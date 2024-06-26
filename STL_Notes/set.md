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

std::set<int> set4 = {1, 2, 3, 4, 5}; // 使用初始化列表来初始化set
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

`find` 方法用于在`std::set`中查找特定的元素。如果找到该元素，则返回一个指向该元素的迭代器；如果未找到，则返回指向集合末尾的迭代器（即`set.end()`）。

**语法：**

```cpp
std::set<int>::iterator it = set1.find(const Key& k);
```

`count` 方法用于统计集合中某个特定元素的数量。由于`std::set`中的每个元素都是唯一的，因此`count` 方法要么返回`0`（表示元素不存在），要么返回`1`（表示元素存在）。

**语法：**

```cpp
size_t count = set1.count(const Key& k);
```

1. 查找元素：
 • `find` 方法在查找元素时效率很高，因为`std::set`底层通常使用平衡二叉树（如红黑树）实现，查找操作的时间复杂度为`O(log n)`。
 • 如果需要访问找到的元素，可以使用find 方法。
2. 统计元素：
 • `count` 方法在统计元素时同样效率很高，因为它只需检查元素是否存在，时间复杂度为`O(log n)`。
 • count 方法特别适用于检查元素是否存在，因为它返回的结果要么是`0`，要么是`1`。
3. 组合使用：
 • 可以组合使用`find` 和 `count` 方法来提高代码的可读性和效率。例如，先使用`count` 检查元素是否存在，然后再使用`find` 来获取元素的迭代器。

```cpp
#include <iostream>
#include <set>

int main() {
    std::set<int> set1 = {1, 2, 3, 4, 5};

    int value = 3;

    // 先检查元素是否存在
    if (set1.count(value) > 0) {
        // 元素存在，使用find获取迭代器
        std::set<int>::iterator it = set1.find(value);
        std::cout << "Element found: " << *it << std::endl;
    } else {
        std::cout << "Element not found" << std::endl;
    }

    return 0;
}
```

## set和multiset的区别

+ `set` 不可以包含重复的元素，而 `multiset` 可以包含重复的元素。
+ `set` 插入数据的同时会返回一个 `pair<iterator, bool>` 类型的值，其中 `iterator` 指向插入的元素，`bool` 表示是否插入成功；而 `multiset` 插入数据的同时只会返回一个 `iterator` 类型的值，指向插入的元素。因此，`multiset` 可以插入重复的元素，而 `set` 不可以。

## pair类型

`pair` 是成对出现的数据结构，它包含两个数据成员，分别为 `first` 和 `second`。`pair` 可以用来存储两个数据的组合。

### 构建pair

```cpp
#include <utility>
pair<int, string> p1(1, "one");
pair<int, string> p2 = make_pair(2, "two");
```

### 访问 `std::pair` 的成员

`std::pair` 的成员可以通过 `first` 和 `second` 来访问。

```cpp
#include <iostream>
#include <utility>
#include <string>

int main() {
    std::pair<int, std::string> p(1, "one");

    std::cout << "First: " << p.first << std::endl;
    std::cout << "Second: " << p.second << std::endl;

    return 0;
}
```

## `set` 容器排序

`set` 容器默认是按升序（从小到大）排序的，如果想要改变排序方式，可以使用自定义的比较函数。在定义`std::set`时，可以指定一个比较函数对象或函数指针来改变排序方式。

```cpp
#include <set>
#include <functional> // 使用标准库提供的比较函数对象`std::greater`

std::set<int, std::greater<int>> set1; // 降序排序
```

也可以使用 lambda 表达式来自定义比较函数：

```cpp
std::set<int, decltype([](int a, int b) { return a > b; })> set1;
```

具体来说，`std::set` 使用的比较函数必须形成一个严格弱序，即对于任意两个元素 `a` 和 `b`，如果比较函数返回 `true`，则 `a` 被认为在 `b` 之前。因此，较大的元素会排在较小的元素前面，从而实现降序排序。