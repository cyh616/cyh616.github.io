---
title: C++ String 库详解
date: 2025-01-18 20:18:00 +0800
categories: [C++基础, 标准库]
tags: [c++, string, 字符串处理]
author: CYH
toc: true
---

# C++ String 库详解

## 1. 基本介绍
```cpp
#include <string>  // C++版本
```
string 库提供了字符串类及其相关操作，是C++标准库中最常用的组件之一。相比C风格字符串，string类更安全、更方便，提供了丰富的字符串处理功能。

## 2. 常用功能

### A. 初始化
```cpp
string str1;                    // 空字符串
string str2 = "hello";         // 直接初始化
string str3(5, 'a');           // "aaaaa"
string str4(str2);             // 拷贝构造
string str5 = str2 + "world";  // 构造并连接
```

### B. 访问和修改
```cpp
string str = "hello";
str[0] = 'H';                  // 通过下标访问（不检查越界）
str.at(0) = 'H';               // 通过at访问（检查越界）
char& front = str.front();     // 首字符引用
char& back = str.back();       // 尾字符引用

// 获取C风格字符串
const char* c_str = str.c_str();  // 返回C风格字符串
```

### C. 长度和容量
```cpp
string str = "hello";
str.length();                  // 字符串长度
str.size();                    // 同length()
str.capacity();               // 当前分配的容量
str.empty();                  // 是否为空
str.clear();                  // 清空字符串
str.shrink_to_fit();         // 释放多余内存
```

### D. 修改操作
```cpp
string str = "hello";
str += " world";              // 追加
str.append(" again");         // 追加
str.push_back('!');          // 追加单个字符
str.pop_back();              // 删除最后一个字符

// 插入
str.insert(5, " my");        // 在位置5插入
str.insert(0, 3, 'x');       // 在开头插入3个'x'

// 删除
str.erase(5, 3);             // 从位置5删除3个字符
str.erase(str.begin() + 5);  // 删除迭代器位置的字符
```

## 3. 实际应用

### A. 字符串查找
```cpp
string str = "hello world";
size_t pos;

// 查找子串
pos = str.find("world");      // 从左向右查找
pos = str.rfind("l");         // 从右向左查找

// 查找字符集合
pos = str.find_first_of("aeiou");   // 查找第一个元音
pos = str.find_last_of("aeiou");    // 查找最后一个元音
pos = str.find_first_not_of(" \t"); // 查找第一个非空白字符

// 检查是否找到
if (pos != string::npos) {
    cout << "Found at: " << pos << endl;
}
```

### B. 字符串处理
```cpp
// 子串提取
string str = "hello world";
string sub = str.substr(0, 5);  // 提取子串 "hello"
string sub2 = str.substr(6);    // 从位置6到末尾

// 字符串分割
vector<string> split(const string& str, char delim) {
    vector<string> tokens;
    string token;
    istringstream tokenStream(str);
    while (getline(tokenStream, token, delim)) {
        tokens.push_back(token);
    }
    return tokens;
}

// 大小写转换
transform(str.begin(), str.end(), str.begin(), ::tolower);
transform(str.begin(), str.end(), str.begin(), ::toupper);
```

### C. 数值转换
```cpp
// 字符串转数字
string num_str = "123.456";
int i = stoi(num_str);        // 转换为整数
double d = stod(num_str);     // 转换为浮点数
long l = stol(num_str);       // 转换为长整型

// 数字转字符串
string s1 = to_string(123);   // 整数转字符串
string s2 = to_string(3.14);  // 浮点数转字符串
```

## 4. 注意事项

### A. 性能优化
```cpp
// 预分配空间
string str;
str.reserve(1000);  // 预分配1000字节空间

// 使用引用避免拷贝
void processString(const string& str) {
    // 处理字符串
}

// 使用移动语义
string getString() {
    string result = "hello";
    return result;  // 编译器会优化为移动语义
}
```

### B. 常见陷阱
1. 下标访问不检查越界，建议使用at()
2. 字符串拼接时注意性能
3. c_str()返回的指针在字符串修改后可能失效
4. 注意string::npos的使用（通常是size_t的最大值）

## 总结
string库提供了丰富的字符串处理功能，主要优点：
1. 内存管理自动化
2. 提供了丰富的操作函数
3. 类型安全
4. 支持现代C++特性

使用建议：
- 优先使用string而不是C风格字符串
- 注意性能关键场景的优化
- 合理使用const引用避免拷贝
- 熟悉常用成员函数

## 参考资料
- [C++ Reference - String](https://en.cppreference.com/w/cpp/string/basic_string)
- [C++ String Tutorials](https://www.cplusplus.com/reference/string/string/)
- [Effective C++ - Scott Meyers](https://www.amazon.com/Effective-Specific-Improve-Programs-Designs/dp/0321334876) 