---
title: 重载
---

C++ 中的函数重载是指在同一个作用域中，可以定义多个同名但参数列表不同的函数。当程序调用重载函数时，编译器会根据函数调用中提供的参数类型和数量，来选择调用哪个函数。

```cpp
#include <iostream>

using namespace std;

void print(int num) {
    cout << "The integer is " << num << endl;
}

void print(double num) {
    cout << "The double is " << num << endl;
}

int main() {
    int i = 5;
    double d = 3.14;

    print(i);
    print(d);

    return 0;
}
```

在上述代码中，定义了两个同名但参数类型不同的函数 print()，分别用于输出整数和浮点数。在主函数中，分别调用了这两个函数，并传递了相应的参数，编译器会根据参数类型来选择调用哪个函数，输出相应的结果。

重载函数的参数列表必须不同，否则编译器无法区分它们，会导致编译错误。此外，重载函数的返回类型可以相同也可以不同，但不能仅仅因为返回类型不同而进行重载。

