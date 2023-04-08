---
title: 指针
---

指针是 C 语言的一个亮点。

指针用于记录某个存储单元的地址。

## 定义

指针的定义、使用如下：

```c
int a = 100;      // 定义变量 a
int *p = &a;      // 定义指针 p 并指向 a
printf("%X", p);  // 以十六进制格式输出 p 的内容，即 a 的地址
printf("%d", *p); // 输出 a 的内容，即 p 所执行的变量的内容 

// 将指针作为函数参数
void swap(int *p1, int *p2) {
    int temp;
    temp = *p1;
    *p1 = *p2;
    *p2 = temp;
}
```

## 数组遍历

指针可以用在数组中，如：

```c
int a[4] = {1, 2, 3, 4}; // 定义数组 a
int *p = a;              // 此时 p 指向 a[0]
p ++;                    // 此时 p 指向 a[1]

// 通过指针遍历数组
for (p = a; p < (a + 4); p ++)
    scanf("%d", *p); 
```

用数组名做参数，等价于用指针做参数，如下两段代码作用是等价的：

```c
// 用数组名做参数
void func(int a[], int n);

// 用指针做参数
int *p = a;
void func(int *p, int n);
```

指针也可以遍历二维数组，如：

```c
int a[3][3] = {    // 二维数组
    {1, 2, 3},
    {4, 5, 6},
    {7, 8, 9}
};
int (*p)[3] = a;   // 指向一维数组的指针变量，注意不是指针数组
for (int i = 0; i < 3; i ++) {
    printf("%d\n", *p[i]);
}
```

## 引用字符串

指针可以用来引用字符串，如：

```c
char *s = "Hello!";
```

## 函数指针

函数名记录着函数的起始地址，可通过函数名调用函数。

由于指针用来记录地址，因此函数也可以用函数指针进行调用，如：

```c
// 定义一个函数 max
int max(int x, int y) {
    return (x > y) ? x : y;
}
int (*p)(int, int) = max; // 定义函数指针指向 max 函数
c = (*p)(a, b);           // 通过函数指针调用函数
```

指针可以作为函数参数，因此函数指针可以作为函数的参数和返回值。

例如 `malloc` 库函数：

```c
void *malloc(unsigned int size);
```

## 指针数组

指针数组是元素都是指针类型的数组。定义和使用如下：

```c
char *name[] = {"Hello", "World"}; // 定义有 2 个元素的指针数组
printf("%s", name[0]);             // 输出第 1 个元素
```

## 二维指针

二维指针是指向一个指针变量的指针。如：

```c
char *name[] = {"Hello", "World"};
char **p = name[0];
```

## 指针应用场景

指针在主函数中常作为形参出现，如：

```c
int main(int argc, char *argv[])
```

其中 argc 是参数的个数，argv 是参数数组，每个元素都是字符串。

main 函数由操作系统调用，参数在命令行中给出。

内存的动态分配也涉及指针，相应的系统库函数包括：

```c
void *malloc(unsigned int size);           // 开辟 size 字节的连续空间
void *calloc(unsigned n, unsigned size);   // 开辟 n 个长度为 size 的连续空间
void *realloc(void *p, unsigned int size); // 重新分配以 p 开头的连续空间
void free(void *p);                        // 释放以 p 开头的连续空间
```