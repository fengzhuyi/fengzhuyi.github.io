---
title: 算法
---

算法库（algorithm）可配合容器使用，下面介绍常用的一些算法。

## 不修改序列的操作

对一个任意的 vector 的操作：

```cpp
num = count(v.begin(), v.end(), x); // 统计 x 的个数
if (find(v.begin(), v.end(), x) != v.end()); // 查找第一个 x
```

## 修改序列的操作

对一个任意的 vector 的操作：

```cpp
rotate(v.begin(), v.begin() + 2, v.end()); // 翻转 
replace(v.begin(), v.end(), old, new); // 用 new 替换所有 old 
swap(x, y); // 交换值
unique(v.begin(), v.end()); // 删除相邻重复元素
reverse(v.begin(), v.end()); // 反转
```

## 分区操作

可采用 partition 函数为对指定范围的元素进行划分。

```cpp
auto cmp = [*first](const auto& e) { return e < *first; };
auto mid = partition(first, last, cmp);
```

函数会返回一个正向迭代器，指向的是第二组数据中的第 1 个元素。

所有比 first 小的元素放在左边，否则放右边。

## 排序操作

```cpp
if (is_sorted(v.begin(), v.end()) == false) {
    sort(v.begin(), v.end()); // 排序
}
```

## 二分查找

针对排好序的 vector 的操作：

```cpp
bool result = binary_search(v.begin(), v.end(), x); // 查找是否包含 x
it = lower_bound(v.begin(), v.end(), x); // 不小于 x 的第一个元素
it = upper_bound(v.begin(), v.end(), x); // 大于 x 的第一个元素
```

## 对有序数组的操作

```cpp
vector<int> v;
merge(v1.begin(), v1.end(), v2.begin(), v2.end(), back_inserter(v)); // 合并
```

## 集合操作

```cpp
vector<int> v1 = {1, 2, 4};
vector<int> v2 = {2, 3};
if (includes(v1.begin(), v1.end(), v2.begin(), v2.end())) // v1 是否包含 v2
set_difference(v1.begin(), v1.end(), v2.begin(), v2.end(), inserter(v, v.begin())); // 差集
set_union(v1.begin(), v1.end(), v2.begin(), v2.end(), inserter(v, v.begin())); // 并集
```

## 堆操作

```cpp
make_heap(v.begin(), v.end()); // 建立堆
if (is_heap(v.begin(), v.end())) // 判断是否为堆
v.push_back(x); // 将元素加入堆尾
push_heap(v.begin(), v.end()); // 结合上一步
pop_heap(v.begin(), v.end()); // 弹出最大元素
v.pop_back(); // 结合上一步
sort_heap(v.begin(), v.end()); // 将堆变成升序数组
```

## 最值

```cpp
e = max(x, y);
e = min(x, y);
e = *max_element(v.begin(), v.end()); // 最大值
e = *min_element(v.begin(), v.end()); // 最小值
```

## 排列

```cpp
is_permutation(v1.begin(), v1.end(), v2.begin()); // v2 是否为 v1 的排列
next_permutation(v.begin(), v.end()); // 下一个排列
```

## 求和

```cpp
sum = accumulate(v.begin(), v.end()); // 求和
```

## 参考链接

- [Algorithms library](https://en.cppreference.com/w/cpp/algorithm)