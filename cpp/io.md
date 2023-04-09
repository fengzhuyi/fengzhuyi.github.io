---
title: 输入输出
---

iostream 是 C++ 标准库中用于输入输出的库，包括了三个流类：istream、ostream 和 iostream。

istream 和 stream 类分别用于输入和输出，iostream 是这两个类的基类，同时也定义了一些公共的操作。

iostream 库提供了多种方式来读取和写入数据，包括从标准输入/输出设备读写，从文件读写，以及从字符串读写等。

以下是一个简单的 iostream 库示例，演示如何从键盘读取数据并将其写入文件：

```cpp
#include <iostream>
#include <fstream>
#include <string>

using namespace std;

int main() {
    string line;
    ofstream myfile("example.txt"); // 打开文件用于写入
    if (myfile.is_open()) { // 如果文件打开成功
        cout << "Enter text. Enter '!' to quit." << endl;
        while (getline(cin, line)) {
            if (line == "!") {
                break;
            }
            myfile << line << endl; // 写入文件
        }
        myfile.close(); // 关闭文件
        cout << "Text written to file." << endl;
    }
    else {
        cout << "Unable to open file." << endl;
    }
    return 0;
}
```