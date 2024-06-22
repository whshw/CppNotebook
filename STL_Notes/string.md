# C++ string类

## 基本概念

`string`是C++标准库中的一个类，用于处理字符串。它支持许多操作，如比较，连接，查找和替换等。

`char*` 是一个指向字符数组的指针，而 `string` 是一个类，它封装了一个字符数组，并提供了许多成员函数来操作这个字符数组。
## 构造函数

```cpp
#include <string>

std::string str1; // 创建一个空的string
std::string str2("Hello"); // 使用C字符串来构造string
std::string str3(str2); // 使用另一个string来复制构造新的string
std::string str4(5, 'a'); // 创建一个包含5个字符'a'的string
```

## 赋值操作

```cpp
str1 = str2; // 将str2的内容赋值给str1
str1 = "Hello"; // 将C字符串赋值给str1
str1 = 'a'; // 将字符赋值给str1
str1.assign(str2); // 使用另一个string来赋值
str1.assign("Hello"); // 使用C字符串来赋值
str1.assign(5, 'a'); // 使用字符'a'来赋值
str1.assign("Hello", 2); // 使用C字符串的前2个字符来赋值
```

## 字符串拼接

```cpp
str1 = str2 + str3; // 使用+运算符连接两个string
str1 += str2; // 使用+=运算符将另一个string添加到str1的末尾
str1.append(str2); // 使用append()函数将另一个string添加到str1的末尾
str1.append("Hello"); // 使用C字符串添加到str1的末尾
str1.append(str2, 2); // 使用另一个string的前2个字符添加到str1的末尾
```

## 字符串查找和替换

```cpp
str1 = "Hello, World!";
int pos = str1.find("Hello"); // 查找子串"Hello"在str1中的位置, 返回第一次出现的位置，如果没有找到则返回`std::string::npos`
pos = str1.find("Hello", 2); // 从位置2开始查找子串"Hello"在str1中的位置
str1.replace(pos, 5, "World"); // 将str1中从pos开始的5个字符替换为"World"
```

## 字符串比较

```cpp
int result = str1.compare(str2); // 比较str1和str2
```

## 字符串存取

```cpp
char ch = str1[0]; // 使用下标运算符访问str1的第一个字符
ch = str1.at(0); // 使用at()函数访问str1的第一个字符
```

## 字符串插入和删除

```cpp
str1.insert(0, "Hello"); // 在str1的开始插入"Hello"
str1.erase(0, 5); // 删除str1的前5个字符
```

## 子串获取

```cpp
std::string sub = str1.substr(0, 5); // 获取str1的前5个字符组成的子串
```