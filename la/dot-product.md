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

假设矩阵 $A$ 将二维空间压缩到单位向量 $\vec{u}$ 所在的数轴 $l$ 上。

单位向量 $\vec{u}$ 的坐标为 $(a, b)$。

## 投影

$\vec{u}$ 的坐标的几何含义如下：

- $\vec{u}$ 投影到 x 轴的值为 $a$。
- $\vec{u}$ 投影到 y 轴的值为 $b$。

由于 $\vec{i},\vec{j},\vec{u}$ 都是单位向量，根据对称性可知：

$\vec{u}$ 投影到 x 轴的值等于 $\vec{i}$ 投影到数轴 $l$ 上的值，即 $\vec{i}$ 在数轴 $l$ 上的投影为 $a$。

$\vec{u}$ 投影到 y 轴的值等于 $\vec{j}$ 投影到数轴 $l$ 上的值，即 $\vec{j}$ 在数轴 $l$ 上的投影为 $b$。

## 非方阵

平面中任意一个向量 $\vec{v}$ 都可以表示为 $\vec{i}, \vec{j})$ 表示。

记 $\vec{v}$ 的坐标为 $(c,d)$。

根据[非方阵](nonsquare-matrix)的几何意义，$\vec{v}$ 在数轴 $l$ 上的投影可由 $1\times2$ 矩阵完成，矩阵的列是基 $(\vec{i}, \vec{j})$ 变换后的值：

$$
\vec{v}\cos\theta=\begin{bmatrix}a&b\end{bmatrix}\begin{bmatrix}c\\d\end{bmatrix}=ac+bd
$$

这就是两种不同计算方式的内在联系。

若 $\vec{u}$ 是非单位向量，可乘以系数 $k$ 进行放缩即可。

## 总结

两个向量点乘，相当于将其中一个向量转化为线性变换，解读方式很新奇。

但如果将向量看作线性变换的物质载体，整个过程就自然多了。