---
title: 等值演算
mathjax: true
---

> 上一章：[命题公式与赋值](/logic/formula)

如果两个公式形式不同，但真值表完全相同，我们称这两个公式`等值`。

举个简单的例子：

$$
A = p \\
B = ¬¬p
$$

显然 A 与 B 等值，即 $A \leftrightarrow B$ 为永真式，记作 $A \Leftrightarrow B$，称 $A \Leftrightarrow B$ 为`等值式`。

## 重要等值式

这里给出 24 个重要等值式，可用真值表验证。

（1）双重否定律

$$
A \Leftrightarrow \neg\neg A
$$

（2）等幂律

$$
A \Leftrightarrow A \lor A \\
A \Leftrightarrow A \land A
$$

（3）交换律

$$
A \lor B \Leftrightarrow B \lor A \\
A \land B \Leftrightarrow B \land A
$$

（4）结合律

$$
(A ∨ B) ∨ C \Leftrightarrow A ∨ (B ∨ C) \\
(A ∧ B) ∧ C \Leftrightarrow A ∧ (B ∧ C)
$$

（5）分配律

$$
A ∨ (B ∧ C) \Leftrightarrow (A ∨ B) ∧ (A ∨ C) \\
A ∧ (B ∨ C) \Leftrightarrow (A ∧ B) ∨ (A ∧ C)
$$

（6）德·摩根律

$$
¬(A ∨ B) \Leftrightarrow ¬A ∧ ¬B \\
¬(A ∧ B) \Leftrightarrow ¬A ∨ ¬B
$$

（7）吸收律

$$
A ∨ (A ∧ B) \Leftrightarrow A \\
A ∧ (A ∨ B) \Leftrightarrow A
$$

（8）零律

$$
A ∨ 1 \Leftrightarrow 1 \\
A ∧ 0 \Leftrightarrow 0
$$

（9）同一律

$$
A ∨ 0 \Leftrightarrow A \\
A ∧ 1 \Leftrightarrow A
$$

（10）排中律

$$
A ∨ ¬A \Leftrightarrow 1
$$

（11）矛盾律

$$
A ∧ ¬A \Leftrightarrow 0
$$

（12）蕴涵等值式

$$
A → B \Leftrightarrow ¬A ∨ B
$$

（13）等价等值式

$$
A ↔ B \Leftrightarrow (A → B) ∧ (B → A)
$$

（14）假言易位

$$
A → B \Leftrightarrow ¬B → ¬A
$$

（15）等价否定等值式

$$
A ↔ B \Leftrightarrow ¬A ↔ ¬B
$$

（16）归谬论

$$
(A → B) ∧ (A → ¬B) \Leftrightarrow ¬A
$$

通过给出的 24 个等值式，可以推演出更多的等值式来。

称由已知的等值式推演出另外一些等值式的过程为`等值演算`。

## 置换规则

置换规则：设 F(A) 是含公式 A 的命题公式，$B \Leftrightarrow A$，若用 B 置换 F(A) 中的 A，得 F(B)，则 $F(B) ⇔ F(A)$。

如证明下面的等值式：

$$
(p → q) → r ⇔ (¬q ∧ p) ∨ r
$$

证明过程如下：

$$
\begin{align}
&\quad\enspace(p → q) → r \\  
&⇔ (¬p ∨ q) → r &\text{蕴涵等值式} \\
&⇔ ¬(¬p ∨ q)r   &\text{蕴涵等值式} \\
&⇔ (p ∧ ¬q) ∨ r &\text{德·摩根律} \\
&⇔ (¬q ∧ p) ∨ r &\text{交换律} \\
\end{align}
$$

## 真值函数

设公式 A 有两个变项，记作 A = F(p, q)。

则定义域为 {00, 01, 10, 11}，值域为 {0, 1}。

将定义域到值域的一个映射称为一个 2 元真值函数，则共有 16 个真值函数。

若 A 有 $n$ 个变项，则定义域有 $2^n$ 个元素，值域有 2 个元素，共有 $2^{2^n}$ 个真值函数。

每个真值函数都对应无数个与其等值的公式。

## 功能完备集

任何公式都可以用 $\\{¬, ∧, ∨, →, ↔ \\}$ 联结多个变项而成，称 $\\{→, ∧, ∨, →, ↔\\}$ 为功能完备集。

根据蕴涵等值式可知，$→$ 能用 $¬$ 与 $∨$ 表示，我们称 $→$ 为冗余的联结词。

若功能完备集没有冗余的联结词，称它为极小的功能完备集，例如 $\\{¬, ∨\\}$ 和 $\\{¬, ∧\\}$。

> 下一章：[析取范式](/logic/dnf)