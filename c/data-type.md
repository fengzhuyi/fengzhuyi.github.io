---
title: 数据类型
---

C 语言有很多基础数据类型，如整数、浮点数等等。

但本文讲的是三种自定义数据类型，分别是结构体、共用体和枚举。

## 结构体

结构体是不同类型数据组成的组合型。声明、定义和使用如下：

```c
struct Person {     // 声明一个 Person 的结构体
    char name[20];
    int age;
};

struct Person feng = {"feng", 20};         // 定义 & 初始化
printf("%s : %d\n", feng.name, feng.age);  // 输出成员变量

struct Person p = feng;   // 使用结构体指针
int name = p->name;       // 获取 feng 的名字
```

链表的节点就是一个结构体，如：

```c
struct Node {
    int data;
    struct Node *next; 
};
```

可以用 typedef 简化 struct 的命名：

```c
typedef struct Node Node; // 将 struct Node 重命名为 Node
Node node;
```

## 共用体

共用体允许同一段内存单元存放不同类型的变量，如：

```c
union Data {
  int a;
  char ch;
};
```

a 和 ch 共用一段内存，Data 的存储空间为 4 个字节。

## 枚举

枚举限制了变量的取值，一个变量只有几种可能的值。如：

```c
enum Weekday {sun, mon, tue, wed, thu, fri, sat};
```