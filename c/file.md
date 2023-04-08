---
title: 文件处理
---

文件是存在磁盘中的数据。

系统会将文件中的数据加载到内存中，然后程序再开始处理数据。

## 文件类型

文件通过 `FILE` 结构体标识，`FILE` 的部分信息如下：

```c
typedef struct {
    unsigned flags;        // 文件状态标志
    char fd;               // 文件描述符
    short bsize;           // 数据缓冲区的大小
    unsigned char *buffer; // 数据缓冲区的位置
} FILE;                    // FILE 定义在 stdio.h 头文件中
```

程序使用文件前需要打开文件，实质上是为文件创建相关的 `FILE` 记录。

程序使用文件后需要关闭文件，实质上是销毁 `FILE` 相关信息，并将内存中的新数据写回磁盘。

```c
FILE *fp = fopen("file", "r");  // 以读的方式打开 file
if (fp == NULL) {
    printf("open failed\n");    // 若打开失败，则提示
} else {
    fclose(fp);                 // 否则关闭文件，关闭成功返回 0
}
```

## 打开方式

文件的打开方式包括读（r）、写（w）和追加（a）。

文件打开后，程序就可以进行相关的文件操作了。

```c
FILE *in = fopen("file1", "r");  // 读的方式打开 file1
FILE *out = fopen("file2", "w"); // 写的方式打开 file2
char ch = fgetc(in);             // 从 file1 中读一个字符到 ch 中
while(ch != EOF) {               // 如果读取成功
    fputc(ch, out);              // 将 ch 写到 file2 中
    putchar(ch);                 // 打印 ch 到屏幕上
    ch = fgetc(in);              // 从 file1 中读下一个字符到 ch 中
}
```

其中 `EOF` 是定义为 -1 的全局变量。

## 字符串读写

C 语言提供了向文件读写一个字符串的函数：

```c
char *fgets(char *s, int n, FILE *fp);
int fputs(char *s, FILE *fp);
```

## 格式化读写

C 语言提供格式化的方式读写文本文件：

```c
int i = 3;
float f = 4.5;
fprintf(fp, "%d, %f", i, f);  // 以 3, 4.5 的格式将数输入文件中 
fcanf(fp, "%d, %f", &i, &f);  // 从文件中将 3 和 4.5 读出来
```

其中 `fprintf` 和 `fscanf` 存在 ASCII 码和二进制码之间的切换，如果内存和磁盘数据交换频繁，尽量不用。

## 二进制读写

可以采用 `fread` 和 `fwrite` 进行二进制的读写。调用形式如下

```c
fread(buffer, size, count, fp);
fwrite(buffer, size, count, fp); 
```

例如读写数组、结构体：

```c
typedef struct Person Person;
float f[10];
fread(f, 4, 10, fp); // 从文件 fp 中读 10 个浮点数

Person feng = {"feng", 20};
fwrite(&feng, sizeof(Person), 1, fp);  // 向文件 fp 中写入 feng 变量
fread(&feng, sizeof(Person), 1, fp);   // 从文件 fp 中读数据到 feng 变量
```

## 随记读写

C 语言支持从任意一个地方读取文件。

```c
// 使文件位置标记返回文件开头
void rewind(FILE *stream); 
rewind(fp);

// 设置偏移位置，fromwhere 有三个值：0, 1, 2
int fseek(FILE *stream, long offset, int fromwhere);
fseek(fp, 100L, 0);  // 向前移到离文件开头 100 个字节处
fseek(fp, 50L, 1);   // 向前移到离当前位置 50 个字节处
fseek(fp, -10L, 2);  // 从文件末尾向后退 10 个字节

// 获取偏移位置，-1 表示函数时出错
long ftell(FILE *stream);
```

## 文件错误

C 提供一些函数用于检查输入输出函数调用时可能出现的错误：

```c
// 执行 fopen 时 ferror 初值自动置 0
int ferror(FILE *stream);
if (ferror(fp)) printf("ferror\n");

// 将 ferror(fp) 置 0
void clearerr(FILE *stream);
clearerr(fp); 
```