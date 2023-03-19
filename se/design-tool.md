---
title: 软件设计工具
mermaid: true
---

软件设计包括所有有助于将需求文档转换为实现的活动。

需求文档指定了软件的所有功能和非功能的需求。

需求文档以人类可读和可理解的文档形式出现，计算机与之无关。

软件设计阶段将人类可读的需求文档转化为技术文档。

程序员可以对照技术文档进行编程。

常用的设计工具包括：

## 1. 伪代码

伪代码的目的是使被描述的算法可以容易地以任何一种编程语言实现。

伪代码必须结构清晰、代码简单、可读性好，并且类似自然语言。

使用伪代码， 不用拘泥于具体实现。

如打印斐波那契数列的伪代码如下

```c
intput n
a = 0
b = 1
for (i = 1; i <= n; i ++) {
  if (a > b) {
    b += a
    print b
  } else {
    a += b
    print a
  }
}
```

## 2. 时序图

序列图是一种交互图，显示流程如何相互操作以及以什么顺序操作。

<div class="mermaid">
sequenceDiagram
    Client-->>Server: Request
    Server-->>Client: Response
    Client-->>Server: Confirm
</div>

## 3. 实体关系图

一种用于数据库设计的结构图。

<div class="mermaid">
erDiagram
    CAR ||--o{ NAMED-DRIVER : allows
    PERSON ||--o{ NAMED-DRIVER : is
</div>

## 4. 类图

在软件工程中，统一建模语言 (UML) 中的类图是一种静态结构图，它通过显示系统的类、它们的属性、方法以及对象之间的关系来描述系统的结构。

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

