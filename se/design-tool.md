---
title: 软件设计工具
mermaid: true
---

> 上一章：[软件设计](/se/design)

软件设计阶段需要输出设计文档、流程图、伪代码等。

以下是一些常用的设计工具。

## 1. 伪代码

伪代码描述的算法结构清晰，可以容易地以任何一种编程语言实现。

使用伪代码， 不用拘泥于具体实现。

如打印斐波那契数列的伪代码：

```c
intput n
a = 0
b = 1
for (i = 1; i <= n; i ++)
  if a > b then
    b += a
    print b
  else
    a += b
    print a
```

## 2. 时序图

描述信息交互，常用于网络请求描述。

<div class="mermaid">
sequenceDiagram
    Client-->>Server: Request
    Server-->>Client: Response
    Client-->>Server: Confirm
</div>

## 3. 实体关系图

表示实体类型、属性之间的联系，常用于数据库设计。

<div class="mermaid">
erDiagram
    CAR ||--o{ NAMED-DRIVER : allows
    PERSON ||--o{ NAMED-DRIVER : is
</div>

## 4. 类图

通过对象之间的关系来描述系统的结构，常用于面向对象编程中。

<div class="mermaid">
classDiagram
    Animal <|-- Duck
    Animal <|-- Fish
    Animal : +int age
    Animal : +String gender
    Animal: +isMammal()
    Animal: +mate()
    class Duck{
        +String beakColor
        +swim()
        +quack()
    }
    class Fish{
        -int sizeInFeet
        -canEat()
    }
</div>

## 5. 数据流图

以图形方式来表达系统的逻辑功能和数据流动，常用于函数式编程中。

数据流图有四种元素：

- 外部实体：数据的外部来源和去处
- 数据加工：处理单元
- 数据存储：信息的静态存储
- 数据流：处理单元的输入或输入

<div class="mermaid">
flowchart LR
  id1[外部实体]--数据流-->id2((数据加工))-->id3[(数据存储)]
</div>

数据流图按层次进行：

- 第 0 层专注于子系统间的数据流动
- 第 1 层专注于子系统内模块之间的数据流动

实体和数据加工需要编号，例如第 0 层的编号是 1、2、3 等，第 1 层的编号则是 1.1、1.2、1.3 或 2.1、2.2、2.3 等。

> 下一章：[用户接口设计](/se/user-interface)