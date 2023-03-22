---
title: 命题逻辑
---

> 上一章：[主析取范式](/logic/dnf)

推理是从前提出发推出结论的思维过程。

在命题逻辑中，前提和结论都是命题公式，重点研究推理中用到的方法。

## 推理

由前提 A 推出结论 B 的形式结构为 A → B。

若有 n 个前提，则推理的形式结构为 

```
(A₁ ∧ A₂ ∧ ··· ∧ Aₙ) → B
```

若形式结构为`永真式`，则称从前提推出结论的`推理正确`，结论是前提的`逻辑结论`。否则称`推理不正确`。

若 A → B 为永真式，则可记作 A ⇒ B。

我们之前学过几种判断永真式的方法：

- 真值表法
- 命题演算
- 主析取范式

## 推理规则

在证明的任何步骤上，可以

- 前提引入：引入前提。
- 结论引入：将结论作为前提引入。
- 置换规则：使用等值式简化公式。

## 推理定律

推理定律指永真蕴涵式。主要有以下 8 条：

```
1. 附加

A ⇒ (A ∨ B)

2. 化简

(A ∧ B) ⇒ A

3. 假言推理

(A → B) ∧ A ⇒ B

4. 拒取式

(A → B) ∧ ¬B ⇒ ¬A

5. 析取三段论

(A ∨ B) ∧ ¬B ⇒ A

6. 假言三段论

(A →B ) ∧ (B → C) ⇒ (A → C)

7. 等价三段论

(A ↔ B) ∧ (B ↔ C) ⇒ (A ↔ C)

8. 构造三段论

(A → B) ∧ (C → D) ∧ (A ∨ C) ⇒ (B ∨ D)
```

除了上述 8 条，每个等值式均产生 2 个推理定律。

例如，由 A ⇔ ¬¬A 可以产生两条推理定律：

```
A ⇒ ¬¬A

¬¬A ⇒ A
```

## 构造证明法

推理的过程中，不断地用前提推出一些结论，并将已经推出的结论作为新的前提，最终得到我们想要的结论。这种方法称为`构造证明法`。

给出以下推理：

```
前提：p → (q ∨ r), ¬s → ¬q, p ∧ ¬s

结论：r
```

推理的证明如下：

```
1. p ∧ ¬s       前提引入
2. p            1 化简
3. ¬s           1 化简
4. p → (q ∨ r)  前提引入
5. q ∨ r        2 4 假言推理
6. ¬s → ¬q      前提引入
7. ¬q           3 6 假言推理
8. r            5 7 析取三段论
```

## 附加前提证明法

若需要证明的结论也是蕴涵式，如：

```
(A₁ ∧ A₂ ∧ ··· ∧ Aₙ) → (A → B)
```

对其等值运算可得：

```
(A₁ ∧ A₂ ∧ ··· ∧ Aₙ ∧ A) → B
```

其中 A 为`附加前提`。

## 归谬法

根据蕴涵等值式可知：

```
(A₁ ∧ A₂ ∧ ··· ∧ Aₙ) → B ⇔ ¬(A₁ ∧ A₂ ∧ ··· ∧ Aₙ ∧ ¬B) 
```

若附加前提 ¬B 和已知前提不相容，则推理的形式结构为永真式，因此推理正确。