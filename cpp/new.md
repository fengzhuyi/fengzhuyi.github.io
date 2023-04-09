---
title: 动态内存
---

C++ 中的动态内存指的是在程序运行时根据需要动态分配的内存空间，通常使用 new 操作符来动态分配内存，使用 delete 操作符释放动态分配的内存。

使用动态内存分配可以让程序在运行时根据需要分配内存空间，而不需要在编写程序时确定内存空间的大小，这样可以提高程序的灵活性和效率。

以下是一个动态分配数组的例子：

```cpp
int size = 10;
int* arr = new int[size]; // 动态分配数组

// 对数组进行操作

delete[] arr; // 释放动态分配的数组空间

```

动态分配的内存空间必须手动释放，否则会导致内存泄漏，严重的情况可能会导致程序崩溃。

我的建议是，能用容器尽量使用容器，尽量不要自己管理内存。