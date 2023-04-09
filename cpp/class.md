---
title: 类和对象
---

在 C++ 中，类是一种用户自定义的数据类型，它可以封装数据和函数。对象是类的一个实例，它可以访问类中的成员变量和成员函数。C++ 中定义类的基本语法格式如下：

```
class 类名 {
public: // 访问修饰符，指定成员变量和成员函数的访问权限
    成员变量声明;
    成员函数声明;
private: // 访问修饰符，指定成员变量和成员函数的访问权限
    成员变量声明;
    成员函数声明;
};
```

其中，public 和 private 是访问修饰符，它们指定了成员变量和成员函数的访问权限。public 成员可以在类的外部访问，private 成员只能在类的内部访问。

例如，以下是一个表示学生的类的定义：

```cpp
class Student {
public:
    int id;
    string name;
    void printInfo() {
        cout << "id: " << id << ", name: " << name << endl;
    }
};
```

在使用类时，需要通过类定义对象，例如：

```cpp
Student s; // 定义 Student 类型的对象 s
s.id = 1; // 设置对象的成员变量
s.name = "Tom";
s.printInfo(); // 调用对象的成员函数
```

类的成员函数可以访问对象的成员变量，并且可以访问同类的其他对象的成员变量。可以通过 this 指针来访问当前对象的成员变量和成员函数，例如：

```cpp
class Student {
public:
    int id;
    string name;
    void setId(int id) {
        this->id = id; // 使用 this 指针访问对象的成员变量
    }
    void printInfo() {
        cout << "id: " << id << ", name: " << name << endl;
    }
};
```

在上面的例子中，setId 函数使用 this 指针访问当前对象的成员变量 id。