---
title: 泛型
---

C++ 泛型是指一种编程技术，可以使程序在不知道要操作的具体数据类型的情况下，编写通用的代码，从而提高代码的重用性和可扩展性。

C++ 中的泛型主要通过模板（template）实现。模板是一种通用的代码框架，可以在编译时根据具体的数据类型实例化为不同的代码。模板分为函数模板和类模板两种。

## 函数模板

函数模板是一种通用的函数定义，可以处理多种不同的数据类型。函数模板的语法如下：

```cpp
template <typename T>
T function_name(T arg1, T arg2, ...) {
  // 函数体
}
```

其中 typename 是关键字，T 是一个类型参数，可以用于指定函数参数和返回值的类型。函数体中的参数和返回值类型都可以使用 T 来表示。

## 类模板

类模板是一种通用的类定义，可以处理多种不同的数据类型。类模板的语法如下：

```cpp
template <typename T>
class class_name {
  // 类成员和方法
};
```

其中 typename 是关键字，T 是一个类型参数，可以用于指定类的成员变量和成员方法的数据类型。

## 样例

下面是一个使用模板实现的例子：

```cpp
#include <iostream>

// 函数模板
template <typename T>
T max(T a, T b) {
  return a > b ? a : b;
}

// 类模板
template <typename T>
class MyArray {
public:
  MyArray(int size) : size_(size), arr_(new T[size]) {}
  ~MyArray() { delete[] arr_; }

  T& operator[](int index) { return arr_[index]; }

private:
  int size_;
  T* arr_;
};

int main() {
  std::cout << max(3, 5) << std::endl; // 输出 5
  std::cout << max(3.0, 5.0) << std::endl; // 输出 5

  MyArray<int> arr(10);
  for (int i = 0; i < 10; ++i) {
    arr[i] = i;
  }

  for (int i = 0; i < 10; ++i) {
    std::cout << arr[i] << " ";
  }
  std::cout << std::endl;

  return 0;
}
```