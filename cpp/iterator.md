---
title: 迭代器
---

在 C++ 中，迭代器是一种抽象的数据类型，用于提供对容器元素的访问方式。迭代器提供了类似指针的接口，可以遍历容器中的元素，而无需了解底层数据结构的细节。迭代器的实现方式与所操作的容器类型相关。

C++ STL 中的迭代器分为五种类型：前向迭代器、双向迭代器、随机访问迭代器、输入迭代器和输出迭代器。

每种迭代器都具有不同的能力和限制，可用于不同类型的容器和算法中。

本文介绍最常用的前三种。

## 前向迭代器

C++中的前向迭代器是一种迭代器类型，它能够在一个集合中按顺序遍历所有元素，并且只支持前向遍历。

前向迭代器的行为类似于指向单向链表的指针，可以顺序访问每个元素，但不能回溯到前面的元素。

前向迭代器是一种较低级别的迭代器类型，通常用于访问顺序容器中的元素，如链表和队列。

```cpp
#include <iostream>
#include <forward_list>

using namespace std;

int main() {
    // 创建前向列表并添加元素
    forward_list<int> mylist = { 1, 2, 3, 4, 5 };

    // 创建前向迭代器并遍历列表
    forward_list<int>::iterator it;
    for (it = mylist.begin(); it != mylist.end(); ++it) {
        cout << *it << " ";
    }
    cout << endl;

    return 0;
}
```

## 双向迭代器

双向迭代器可以在一个集合中按顺序遍历所有元素，并支持前向和后向遍历。双向迭代器类似于指向双向链表的指针，可以在容器中向前或向后移动。

双向迭代器具有前向迭代器的所有功能，并增加了向后遍历容器的能力，因此它们在许多标准库算法和容器中都得到广泛使用。例如，可以使用双向迭代器在双向链表中遍历元素或删除容器中的元素。

```cpp
#include <iostream>
#include <list>

using namespace std;

int main() {
    // 创建列表并添加元素
    list<int> mylist = { 1, 2, 3, 4, 5 };

    // 创建双向迭代器并遍历列表
    list<int>::iterator it;
    for (it = mylist.begin(); it != mylist.end(); ++it) {
        cout << *it << " ";
    }
    cout << endl;

    // 反向遍历列表
    list<int>::reverse_iterator rit;
    for (rit = mylist.rbegin(); rit != mylist.rend(); ++rit) {
        cout << *rit << " ";
    }
    cout << endl;

    return 0;
}
```

## 随机访问迭代器

随机访问迭代器是一种在迭代器范围内支持随机访问的迭代器。它们允许您在常量时间内移动迭代器，并在常量时间内访问迭代器指向的元素，从而支持随机访问。

标准库中的 vector 和 deque 是使用随机访问迭代器实现的。

```cpp
#include <iostream>
#include <vector>

using namespace std;

int main() {
    // 创建向量并添加元素
    vector<int> myvector = { 1, 2, 3, 4, 5 };

    // 创建随机访问迭代器并遍历向量
    vector<int>::iterator it;
    for (it = myvector.begin(); it != myvector.end(); ++it) {
        cout << *it << " ";
    }
    cout << endl;

    // 通过索引访问向量元素
    cout << "Element at index 2: " << myvector[2] << endl;

    return 0;
}
```