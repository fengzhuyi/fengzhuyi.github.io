---
title: 软件设计
---

> 上一章：[软件需求](/se/requirement)

需求文档不能直接用于开发实现，软件设计阶段需要给出更具体、更专业的设计方案。

## 架构设计

软件架构（software architecture）就是软件的基本结构。

架构设计将软件抽象成多个模块组成的系统。

常见的软件架构有分层架构、微内核架构。

分层架构常用于 iOS 应用开发，如 MVC 模式。

微内核架构常用于操作的开发。

## 功能模块

模块化是一种将软件系统划分为多个离散且独立的模块的技术。

模块化设计遵循了`分而治之`的思想，优势在于：

- 模块更易于维护。
- 模块可以根据功能进行划分。
- 模块可以重复使用。
- 可以实现多个模块并发执行。

程序员需要分析哪些模块可以并行执行。

## 高内聚低耦合

当一个软件程序被模块化时，它的任务根据一些特征被分成几个模块。

模块是为了完成某些任务而组合在一起的代码。

`耦合`与`内聚`用来衡量模块设计的质量。

内聚定义了模块元素内的内部依赖性程度。内聚越大，程序设计越好。

同一个模块的代码服务于同一个功能是最理想的，称为功能内聚。

耦合定义了程序模块之间相互依赖程度。耦合度越低，程序越好。理想情况下，没有耦合被认为是最好的。

耦合可分为以下几类：

- 内容耦合：模块 A 直接修改模块 B 的内容。
- 公共耦合：多个模块访问统一全局数据。
- 控制耦合：模块 A 决定模块 B 的功能。

## 输出验证

软件设计阶段的输出是设计文档、伪代码、逻辑图、流程图等，这些输出包含所有功能和非功能需求的详细描述。

软件设计有可能出现错误，因此最后需要对全部输出进行验证。

越早发现错误越好。

> 下一章：[软件设计工具](/se/design-tool)