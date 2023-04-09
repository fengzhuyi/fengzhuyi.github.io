---
title: 匿名函数
---

函数是代码块，接收输入，产生输出。

除了继承 [C 语言的函数结构](/c/function)外，C++ 增加了[引用类型](/cpp/data-type)和匿名函数。

[引用类型](/c/data-type)之前讲过，本文主要将匿名函数。

## 匿名函数

匿名函数也称 Lambda 表达式，C++ 允许代码中定义简单的函数对象，从而简化代码和提高代码可读性。

Lambda 表达式的基本语法格式如下：

```
[capture](parameters) -> return_type {
    // 函数体
}
```

其中，capture 指定了 Lambda 表达式访问外部作用域变量的方式；parameters 指定了 Lambda 表达式的参数列表；return_type 指定了 Lambda 表达式的返回值类型；函数体则是具体实现功能的代码。

需要注意的是，Lambda 表达式可以访问其所在作用域中的变量，并且可以通过 capture 指定访问方式。capture 可以是 = 或 &，分别表示按值和按引用访问变量。例如：

```cpp
int x = 1, y = 2;
auto sum = [x, &y]() -> int {
    return x + y;
};
```