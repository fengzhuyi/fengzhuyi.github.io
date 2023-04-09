---
title: 容器
---

C++ 标准库提供了多种容器，它们是一种存储和管理对象的数据结构。每种容器都具有不同的特性和用途，可以根据具体的需求选择合适的容器。以下是 C++ 中常用的容器：

- 顺序容器（vector, deque, list）
- 关联容器（map, set）
- 容器适配器（stack, queue, priority queue）

## vector

vector 是动态数组，定义和初始化如下：

```cpp
vector<int> array;        // 长度为 0 的数组
vector<int> array(10);    // 10 个值为 0 的数组
vector<int> array(10, 4); // 10 个值为 4 的数组
vector<vector<int>> matrix(10, vector<int>(10)); // 10*10 的二维数组
```

常用操作如下：

```cpp
array.push_back(100);             // 往数组末尾添加元素
array.emplace_back(20);           // 和 push_back 作用相同，实现不一样
array.insert(array.begin(), 10);  // 往数组头部插入数据
array.insert(array.begin()+2, 4); // 将 4 插入到第 3 个位置 
int elem = array.front();         // 获取数组的第一个元素
unsigned long len = array.size(); // 获取数组的长度
array.pop_back();                 // 删除末尾元素
array.clear();                    // 清空数组
```

常用遍历方法如下：

```cpp
// 按下标访问元素
for (int i = 0; i < array.size(); i ++)
    cout << array[i] << endl;

// 迭代访问
for (auto elem: array)
    cout << elem << endl;
```

## deque

deque 是双端队列，两端皆可插入和删除数据，同时支持随机访问。

定义和初始化如下：

```cpp
deque<int> dq;
```

常用操作如下：

```cpp
dq.push_back(2);
dq.push_front(1);
int first = dq[0];
unsigned long size = dq.size();
dq.pop_back();
dq.pop_front();
```

遍历方法如下：

```cpp
for (auto e: dq) cout << e << endl;
for (int i = 0; i < dq.size(); i ++) {
    cout << dq[i] << endl;
}
```

## list

list 是双向链表，定义和初始化如下：

```cpp
list<int> l;                        // 创建空链表
list<int> l1(3,2);                  // 含有 2 个值为 2 的元素
list<int> l2(l1,begin(), l1.end()); // 复制 l1 的内容给 l2
```

操作方法如下：

```cpp
l.push_back(1);         // 往末尾加入 1
l.push_back(2);         // 往末尾加入 2
l.push_back(4);         // 往末尾加入 4
l.push_back(2);         // 往末尾加入 2
l.unique();             // 删除相邻的重复元素
l.insert(l.begin(), 0); // 往开头插入元素
l.sort();               // 排序
l.remove(2);            // 删除值为 2 的节点
l.erase(l.begin());     // 删除第 1 个节点
```

遍历方法如下：

```cpp
for (auto e: l) cout << e << endl;
```

## map

map 是字典，可通过键（key）快速找到值（value）， 定义和初始化如下

```cpp
map<int, string> map;  // 空字典
map<int, string> map = {
    {1, "hello"},
    {2, "world"},
    {3, "!"}
}; // 给字典赋初值
```

操作方法如下：

```cpp
map.insert({1, "first"});  // 插入 (1, first)
map[3] = "third";          // 插入 (3, third)
map.erase(3);              // 删除 map 的第一个元素
```

遍历方法如下：

```cpp
for (auto [k, v]: map)
    cout << k << " : " << v << endl;
```

## set

set 是集合，内部的元素不重复。定义和初始化如下：

```cpp
set<int> s;
```

操作方法如下：

```cpp
s.insert(1);  // 加入元素 1
s.insert(2);  // 加入元素 2
if (s.find(1) != s.end()) {
    cout << "1 is in set." << endl;
}
s.erase(1);   // 删除元素 1
```

遍历方法如下：

```cpp
for (auto e: s) cout << e << endl;
```

## stack

stack 是栈，定义和使用方法如下：

```cpp
stack<int> s;        // 定义栈
s.push(1);           // 将 1 压入栈
s.push(2);           // 讲 2 压入栈
int e = s.top();     // 获取栈顶元素
s.pop();             // 弹出栈顶元素
auto len = s.size(); // 获取栈的长度
```

遍历方法如下：

```cpp
while (!s.empty()) {
    auto e = s.top();
    s.pop();
    cout << e << endl;
}
```

## queue

queue 是队列，定义和使用方法如下：

```cpp
queue<int> q;        // 定义队列
q.push(1);           // 将 1 压入队列
q.push(2);           // 将 2 压入队列
int e = q.front();   // 获取队头元素
q.pop();             // 弹出队头元素
auto len = q.size(); // 获取队列长度
```

遍历方法如下：

```cpp
while (!q.empty()) {
    auto e = q.front();
    q.pop();
    cout << e << endl;
}
```

## priority queue

priority queue 实质上是堆，头文件在 `queue`，定义和使用方法如下：

```cpp
priority_queue<int> q; // 定义
q.push(1);             // 压入 1
q.push(5);             // 压入 5
q.push(3);             // 压入 3
q.push(8);             // 压入 8
int e = q.top();       // 获取堆顶元素，默认最大堆，所以是 8
q.pop();               // 弹出堆顶元素
auto len = q.size();   // 获取堆的大小
```

priority queue 默认是最大堆：

```cpp
priority_queue<int> q;                             // 最大堆
priority_queue<int, vector<int>, less<int>> q;     // 最大堆，同上一句作用一样
priority_queue<int, vector<int>, greater<int>> q;  // 最小堆
```

第三个参数是确定一个元素的大小，如果元素是自定义结构体，就需要自己构造第三个参数。

以结构体 Person 为例：

```cpp
struct Person {
    string name;
    int age;
    Person(string name, int age): name(name), age(age) {}
};
```

如果我们要以 age 做比较，age 越大元素越大的话，需要构造仿函数，如下：

```cpp
struct Less {
    bool operator() (const Person& a, const Person b) const {
        return a.age < b.age;
    }
};
```

然后就可以使用最大堆了，如下：

```cpp
priority_queue<Person, vector<Person>, Less> q;  // 定义最大堆
q.push(Person("david", 24));                     // 插入元素
q.push(Person("mary", 22));                      // 插入元素
q.push(Person("tom", 32));                       // 插入元素
auto e = q.top();                                // 获取堆顶元素 tom
```