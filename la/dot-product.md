---
title: 点积
mathjax: true
---

在物理学中点积（Dot Product）定义如下：

$$
\vec{v}\cdot\vec{w} = |\vec{v}|\cdot|\vec{w}|\cos\theta
$$

在平面坐标系中点积（Dot Product）计算过程如下：

$$
\begin{bmatrix}1\\2\end{bmatrix}\cdot
\begin{bmatrix}3\\4\end{bmatrix}=
1\cdot 3 + 2 \cdot 4
$$

本文探讨以上两种计算方式的内在联系。

## 前提

假设单位向量 $\vec{u}$ 的坐标为 $(a, b)$。

矩阵 $A$ 将二维空间压缩到单位向量 $\vec{u}$ 所在的数轴 $l$ 上。

## 投影矩阵

$\vec{u}$ 的坐标的几何含义如下：

- $\vec{u}$ 投影到 x 轴的值为 $a$。
- $\vec{u}$ 投影到 y 轴的值为 $b$。

由于 $\vec{i},\vec{j},\vec{u}$ 都是单位向量，根据对称性可知：

- $\vec{i}$ 投影到 $l$ 轴的值为 $a$。
- $\vec{j}$ 投影到 $l$ 轴的值为 $b$。

即 $\begin{bmatrix}a&b\end{bmatrix}$ 为二维空间到数轴 $l$ 的投影矩阵 $A$。

## 投影

平面中任意一个向量 $\vec{v}$ 都可以用 $(\vec{i}, \vec{j})$ 表示。

记 $\vec{v}$ 的坐标为 $(c,d)$。

根据[非方阵](nonsquare-matrix)的几何意义，$\vec{v}$ 在数轴 $l$ 上的投影可由矩阵 $A$ 完成：

$$
\begin{bmatrix}a&b\end{bmatrix}\begin{bmatrix}c\\d\end{bmatrix}=ac+bd
$$

此时 $\vec{i},\vec{j},\vec{v}$ 都在数轴上，即共线。

## 任意两个向量的点积

若 $\vec{w}$ 任意向量，只需要进行数乘运算，将其转化为 $k\vec{u}$ 即可。

因此任意向量 $\vec{v}$ 和 $\vec{w}$ 的点积可表示为：

$$
\vec{v}\cdot\vec{w} = k\vec{u}\vec{v}
$$

## 总结

两个向量点乘，相当于将其中一个向量转化为线性变换，解读方式很新奇。

但如果将向量看作线性变换的物质载体，整个过程就自然多了。