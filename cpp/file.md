---
title: 文件读写
---

类比 [iostream](/cpp/io) 库，fstream 是一个用于读写文件的标准库类。fstream 类是 ifstream 和 ofstream 两个类的基类，因此它既可以读取文件，也可以写入文件。

创建一个 fstream 对象时，需要指定文件名和打开方式。fstream 的打开方式有三种：

- in：以读取方式打开文件。
- out：以写入方式打开文件。
- app：以追加写入方式打开文件。

除此之外，fstream 还有一些其他的打开方式，比如二进制方式打开文件，读写方式打开文件等。

打开文件成功后，就可以使用流操作符 `<<` 和 `>>` 来读写文件内容了。

下面是一个使用 fstream 读写文件的例子：

```cpp
#include <fstream>
#include <iostream>
using namespace std;

int main() {
    // 打开文件并写入数据
    ofstream outfile("example.txt");
    if (!outfile.is_open()) {
        cerr << "Cannot open file!" << endl;
        return 1;
    }
    outfile << "Hello, world!" << endl;
    outfile.close();

    // 读取文件并输出数据
    ifstream infile("example.txt");
    if (!infile.is_open()) {
        cerr << "Cannot open file!" << endl;
        return 1;
    }
    string line;
    while (getline(infile, line)) {
        cout << line << endl;
    }
    infile.close();

    return 0;
}
```