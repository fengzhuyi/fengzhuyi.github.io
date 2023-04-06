---
title: 线性组合
mathjax: true
---

给出两个向量：

$$
\vec{i} = \begin{bmatrix}1\\0\end{bmatrix},\ \vec{j} = \begin{bmatrix}0\\1\end{bmatrix}
$$

则平面直角坐标系上任意一个向量 $\vec{v}$ 都可以用 $\vec{i}$ 和 $\vec{j}$ 表示：

$$
\vec{v} = x\cdot \vec{i} + y\cdot\vec{j} = \begin{bmatrix}x\\y\end{bmatrix}
$$

称 $\vec{i}$ 和 $\vec{j}$ 为坐标系的基向量（Basis Vectors）。

称 $\vec{v}$ 被称为这两个向量的线性组合（Linear Combination）。

所有 $\vec{v}$ 组成的集合称为 $\vec{i}$ 和 $\vec{j}$ 张成的空间（Span）。

## 线性无关

事实上，基不是唯一的，可以用以下两个向量作为基：

$$
\vec{v} = \begin{bmatrix}2\\0\end{bmatrix},\ \vec{w} = \begin{bmatrix}1\\1\end{bmatrix}
$$

坐标系上的任意一个向量都可以用 $\vec{v}$ 和 $\vec{w}$ 来表示。

这两个向量线性无关（Linearly Independent）。

## 线性相关

但是并非任意两个向量都适合作为基，如 $\vec{v}$ 和 $\vec{w}$ 共线：

$$
\vec{v} = \begin{bmatrix}2\\0\end{bmatrix},\ \vec{w} = \begin{bmatrix}1\\0\end{bmatrix}
$$

此时 $\vec{v}$ 和 $\vec{w}$ 张成的空间是 $x$ 轴，不能表示 $x$ 轴之外的向量。

因此称这两个线性相关。