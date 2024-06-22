# C++ deque容器

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

## 大小操作

对于`deque`容器的大小进行操作。

使用`empty()`函数来判断`deque`是否为空：

```cpp
std::deque<int> deque1;
if (deque1.empty()) {
    std::cout << "deque1 is empty" << std::endl;
}
```
使用`size()`函数来获取`deque`中元素的个数：

```cpp
std::deque<int> deque1(5, 10);
std::cout << "deque1 size: " << deque1.size() << std::endl; // 输出：deque1 size: 5
```
`deque`容器没有容量的概念，因此不支持`capacity()`函数。

使用`resize(num)`函数来改变`deque`的大小，若容器变长，则以默认值填充新元素；若容器变短，则删除超出容器大小的元素：

```cpp
std::deque<int> deque1(5, 10);
deque1.resize(10); // 将deque1的大小改变为10
```

使用`resize(num, value)`函数来改变`deque`的大小，并以`value`填充新元素：

```cpp
std::deque<int> deque1(5, 10);
deque1.resize(10, 20); // 将deque1的大小改变为10，并用20填充新元素
```

## 插入和删除操作

向`deque`容器中插入和删除元素。

使用`push_back()`函数在`deque`的尾部插入一个元素：

```cpp
std::deque<int> deque1;
deque1.push_back(10); // 在deque1的尾部插入一个元素10
```

使用`push_front()`函数在`deque`的头部插入一个元素：

```cpp
std::deque<int> deque1;
deque1.push_front(10); // 在deque1的头部插入一个元素10
```

使用`pop_back()`函数删除`deque`尾部的元素：

```cpp
std::deque<int> deque1(5, 10);
deque1.pop_back(); // 删除deque1尾部的元素
```

使用`pop_front()`函数删除`deque`头部的元素：

```cpp
std::deque<int> deque1(5, 10);
deque1.pop_front(); // 删除deque1头部的元素
```

使用`insert(pos, elem)`函数在指定位置插入元素：

```cpp
std::deque<int> deque1(5, 10);
deque1.insert(deque1.begin() + 2, 20); // 在deque1的第3个位置插入一个元素20
```

使用`insert(pos, n, elem)`函数在指定位置插入`n`个元素：

```cpp
std::deque<int> deque1(5, 10);
deque1.insert(deque1.begin() + 2, 3, 20); // 在deque1的第3个位置插入3个元素20
```

使用`insert(pos, first, last)`函数在指定位置插入另一个`deque`的元素：

```cpp
std::deque<int> deque1(5, 10);
std::deque<int> deque2(3, 20);
deque1.insert(deque1.begin() + 2, deque2.begin(), deque2.end()); // 在deque1的第3个位置插入deque2的元素
```

使用`erase(pos)`函数删除指定位置的元素：

```cpp
std::deque<int> deque1(5, 10);
deque1.erase(deque1.begin() + 2); // 删除deque1的第3个元素
```

使用`erase(first, last)`函数删除指定范围内的元素：

```cpp
std::deque<int> deque1(5, 10);
deque1.erase(deque1.begin() + 2, deque1.begin() + 4); // 删除deque1的第3到第4个元素
```

使用`clear()`函数删除`deque`中的所有元素：

```cpp
std::deque<int> deque1(5, 10);
deque1.clear(); // 删除deque1中的所有元素
```

## 数据存取

访问`deque`容器中的元素。

使用`[]`运算符访问`deque`中的元素：

```cpp
std::deque<int> deque1(5, 10);
std::cout << deque1[2] << std::endl; // 输出：10
```

使用`at()`函数访问`deque`中的元素，若访问越界则抛出异常：

```cpp
std::deque<int> deque1(5, 10);
std::cout << deque1.at(2) << std::endl; // 输出：10
```

使用`front()`函数访问`deque`头部的元素：

```cpp
std::deque<int> deque1(5, 10);
std::cout << deque1.front() << std::endl; // 输出：10
```

使用`back()`函数访问`deque`尾部的元素：

```cpp
std::deque<int> deque1(5, 10);
std::cout << deque1.back() << std::endl; // 输出：10
```

## 排序操作

对`deque`容器中的元素进行排序。

使用`sort()`函数对`deque`中的元素进行排序：

```cpp
std::deque<int> deque1 = {3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5};
std::sort(deque1.begin(), deque1.end()); // 对deque1中的元素进行排序
```

## 打印操作

打印`deque`容器中的元素。

使用`for`循环遍历`deque`中的元素：

```cpp
std::deque<int> deque1 = {3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5};
for (int i = 0; i < deque1.size(); i++) {
    std::cout << deque1[i] << " ";
}
std::cout << std::endl;
```

使用迭代器遍历`deque`中的元素：

```cpp
std::deque<int> deque1 = {3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5};
for (std::deque<int>::iterator it = deque1.begin(); it != deque1.end(); it++) {
    std::cout << *it << " ";
}
std::cout << std::endl;
```

