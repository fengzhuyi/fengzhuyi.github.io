---
title: 向量是什么
mathjax: true
---

> 收录于 [线性代数](/la/)

向量（Vector）是[线性代数（Linear Algebra）](/la/)中最重要的概念之一。

本文让大家对向量有一个直观的认识。

## 几何表示

在物理学中，既有大小又有方向的物理量被称为向量，例如速度、力。

我们可以用带方向的箭头来表示一个向量，箭头的长度表示向量的大小。

在平面直角坐标系中，将箭头起点固定在原点，则箭头和坐标一一对应。

若箭头指向坐标 $(x,y)$，则可将该向量表示为：

$$
\vec{v}=\begin{bmatrix}x \\ y\end{bmatrix}
$$

此时向量的长度是 $\sqrt{x^2+y^2}$。

## 线性运算

向量的线性运算包括：

- 向量加法（Vector Addtion）
- 向量数乘（Scalar Multiplication）。

为了直观讲解这两个概念，我给出标量 $k=2$，以及两个向量：
 
$$
\vec{v}=\begin{bmatrix}3 \\ -5\end{bmatrix}, \ \vec{w}=\begin{bmatrix}2 \\ -1\end{bmatrix}
$$

则向量加法 $\vec{v}+\vec{w}$ 的计算过程如下：

$$
\vec{v} + \vec{w} = \begin{bmatrix}3+2 \\ -5+1\end{bmatrix}
$$

向量数乘 $k\vec{v}$ 的计算过程如下：

$$
k\vec{v} = \begin{bmatrix}2 \cdot 3 \\ 2 \cdot (-5)\end{bmatrix}
$$

从物理角度上看，把向量比作力，则：

- 向量相加代表合力，方向和大小发生改变。
- 向量数乘代表力的方向不变，力的大小发生变化。

> 下一章：[线性组合](/la/linear-combination)