---
title: 异常处理
---

C++ 异常处理是一种在程序执行期间遇到异常情况时，抛出异常并捕获该异常的机制。异常是指程序运行时遇到的错误或意外情况，如除以零、访问非法内存等。使用异常处理机制可以使程序更加健壮和可靠。

在 C++ 中，可以使用 try-catch 块来捕获异常。try 块包含可能会抛出异常的代码，catch 块用于捕获异常并执行相应的处理逻辑。如果 try 块中的代码抛出异常，则程序将跳转到与该异常匹配的 catch 块中，如果没有找到匹配的 catch 块，则程序将终止并显示错误信息。

以下是一个简单的示例，演示了如何使用 try-catch 块来捕获异常：

```cpp
#include <iostream>
using namespace std;

int main() {
    int a, b;
    cout << "Enter two numbers: ";
    cin >> a >> b;
    try {
        if (b == 0) {
            throw "Division by zero!";
        }
        cout << "Result: " << a / b << endl;
    }
    catch (const char* msg) {
        cerr << "Error: " << msg << endl;
    }
    return 0;
}
```

在上面的代码中，如果用户输入的第二个数是 0，则会抛出一个字符串异常，程序将跳转到 catch 块中，并输出错误信息。

除了使用字符串作为异常类型外，还可以使用任何其他类型的异常。也可以定义自己的异常类型，并在 catch 块中捕获它们。在 catch 块中可以使用多个 catch 块来捕获不同类型的异常，以便执行不同的处理逻辑。