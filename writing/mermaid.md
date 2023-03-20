---
title: 流程图
mermaid: true
---

流程图由 [Mermaid](https://mermaid.js.org/) 提供支持，样例如下

<div class="mermaid">
graph LR
    A --- B
    B-->C[fa:fa-ban forbidden]
    B-->D(fa:fa-spinner);
</div>

在文章开头需要打开 Mermaid 功能，如下：

```
---
mermaid: true
---
```