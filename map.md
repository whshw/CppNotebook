# C++ map容器

## 基本概念

`map`是一种关联容器，它存储的元素是键值对，键和值可以是任何类型。在`map`中，键是唯一的，因为它们用于对值进行排序和检索。所有元素按键的升序排列。底层结构是用红黑树实现。

## 构造和赋值

```cpp
#include <map>

std::map<int, std::string> map1; // 创建一个空的map
std::map<int, std::string> map2(map1); // 使用另一个map来复制构造新的map

map1 = map2; // 将map2的内容赋值给map1
```

## 大小和交换

```cpp
size_t size = map1.size(); // 返回map中元素的数量
bool isEmpty = map1.empty(); // 检查map是否为空

map1.swap(map2); // 交换map1和map2的内容
```

## 插入和删除

```cpp
map1.insert(std::pair<int, std::string>(1, "one")); // 在map中插入一个元素
map1.insert(std::make_pair(2, "two")); // 使用make_pair()函数插入一个元素
map1.insert(map<int, std::string>::value_type(3, "three")); // 使用value_type插入一个元素
map1[4] = "four"; // 使用下标运算符插入一个元素
map1.erase(1); // 从map中删除键为1的元素
map1.erase(map1.begin()); // 删除map的第一个元素
map1.erase(map1.begin(), map1.end()); // 删除map的所有元素
```

## 查找和统计

```cpp
std::map<int, std::string>::iterator it = map1.find(1); // 查找键为1的元素
size_t count = map1.count(1); // 统计键为1的元素的数量
```

## 排序

`map`容器的元素默认按键的升序排列。如果你想改变排序方式，你可以在创建`map`时提供自定义的比较函数。

```cpp
// 自定义比较函数
struct cmp {
    bool operator() (const int& a, const int& b) const {
        return a > b;
    }
};

std::map<int, std::string, cmp> map3; // 创建一个元素按键的降序排列的map
```