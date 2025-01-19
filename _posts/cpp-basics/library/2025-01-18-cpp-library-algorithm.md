---
title: C++ Algorithm 库详解
date: 2025-01-18 20:18:00 +0800
categories: [C++基础, 标准库]
tags: [c++, algorithm, stl]
author: CYH
toc: true
---

# C++ Algorithm 库详解

## 1. 基本介绍
```cpp
#include <algorithm>
```
algorithm 库包含了大量常用的算法函数，是 C++ STL 的核心组件之一。

## 2. 常用函数分类

### A. 排序相关
```cpp
// sort：排序
vector<int> vec = {3, 1, 4, 1, 5};
sort(vec.begin(), vec.end());                // 升序
sort(vec.begin(), vec.end(), greater<int>()); // 降序

// 自定义排序
sort(vec.begin(), vec.end(), [](int a, int b) {
    return a > b;  // 降序
});

// 部分排序
partial_sort(vec.begin(), vec.begin() + 3, vec.end()); // 部分排序
```

### B. 查找相关
```cpp
// 查找元素
auto it = find(vec.begin(), vec.end(), value);

// 二分查找
bool exists = binary_search(vec.begin(), vec.end(), value);
auto lower = lower_bound(vec.begin(), vec.end(), value); // 第一个>=value
auto upper = upper_bound(vec.begin(), vec.end(), value); // 第一个>value
```

### C. 最值相关
```cpp
// 最大最小值
int max_val = *max_element(vec.begin(), vec.end());
int min_val = *min_element(vec.begin(), vec.end());

// 最大最小值位置
auto max_pos = max_element(vec.begin(), vec.end());
auto min_pos = min_element(vec.begin(), vec.end());
```

### D. 修改序列
```cpp
// 反转
reverse(vec.begin(), vec.end());

// 填充
fill(vec.begin(), vec.end(), 0);

// 替换
replace(vec.begin(), vec.end(), old_value, new_value);

// 去重
sort(vec.begin(), vec.end());  // 先排序
auto new_end = unique(vec.begin(), vec.end());  // 去重
vec.erase(new_end, vec.end());  // 删除重复元素
```

### E. 数值操作
```cpp
// 累加
int sum = accumulate(vec.begin(), vec.end(), 0);

// 内积
int product = inner_product(v1.begin(), v1.end(), v2.begin(), 0);

// 部分和
partial_sum(vec.begin(), vec.end(), result.begin());
```

## 3. 常用技巧

### A. 配合 Lambda 使用
```cpp
// 自定义比较
sort(vec.begin(), vec.end(), [](const auto& a, const auto& b) {
    return a.value < b.value;
});

// 条件查找
auto it = find_if(vec.begin(), vec.end(), [](int x) {
    return x > 10;
});
```

### B. 性能优化
```cpp
// 避免多次计算end()
auto end = vec.end();
for (auto it = vec.begin(); it != end; ++it) {
    // 使用迭代器
}

// 预留空间
vector<int> vec;
vec.reserve(1000);  // 预分配空间
```

## 4. 实际应用

### A. 常见用法
```cpp
// 快速排序并去重
sort(vec.begin(), vec.end());
vec.erase(unique(vec.begin(), vec.end()), vec.end());

// 找到最大的K个元素
partial_sort(vec.begin(), vec.begin() + k, vec.end());

// 检查是否有序
bool is_sorted = is_sorted(vec.begin(), vec.end());
```

### B. 注意事项
1. 使用前确保迭代器范围有效
2. 注意迭代器失效问题
3. 二分查找要求序列已排序
4. 某些算法可能改变原序列

## 5. 复杂度分析

| 算法 | 时间复杂度 | 空间复杂度 |
|------|------------|------------|
| sort | O(nlogn) | O(logn) |
| find | O(n) | O(1) |
| binary_search | O(logn) | O(1) |
| unique | O(n) | O(1) |
| reverse | O(n) | O(1) |

## 总结
algorithm库提供了丰富的算法函数，合理使用可以：
1. 提高代码效率
2. 增强代码可读性
3. 减少bug出现概率
4. 提升开发效率

## 参考资料
- [C++ Reference](https://en.cppreference.com/w/cpp/algorithm)
- [C++ STL算法](https://www.cplusplus.com/reference/algorithm/)
- [Effective STL](https://www.amazon.com/Effective-STL-Specific-Standard-Template/dp/0201749629) 