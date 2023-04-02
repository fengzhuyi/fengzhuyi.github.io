---
title: 克莱姆法则
mathjax: true
---

克莱姆法则是求解方程组的一种方法，但不是最好的方法。

比如高斯消元法会算得更快。

本文讲克莱姆法则仅仅为了拓展视野。

阅读本文会帮你加深对线性方程组的理解。

## 举例

以下面方程组为例：

$$
\begin{cases}
2x-1y=4\\
0x+1y=2
\end{cases}
$$

用矩阵乘法表示为：

$$
\begin{bmatrix}
2&-1\\0&1
\end{bmatrix}
\begin{bmatrix}
x\\y
\end{bmatrix}=
\begin{bmatrix}
4\\2
\end{bmatrix}
$$

## 几何意义

对线性方程组简化表示为：

$$
A\vec{x}=\vec{v}
$$

几何含义是：有一个向量 $\vec{x}$ 经过线性变换 $A$ 后，和向量 $\vec{v}$ 重合。

$A$ 的行列式若为零，要么无解，要么有无穷个解。

这里只考虑行列式不为零的情况。也就是说只考虑不发生降维的情况，此时结果唯一。

## 面积

将 $A\vec{x}=\vec{v}$ 看作线性变换，则 A 表示变换后都基向量组成的矩阵。

A 的行列式表示面积的伸缩因子。

考虑以 $\vec{i},\vec{j}$ 组成的平行四边形，面积为 1，经过变换 A 后面积变为 $\|A\|\cdot 1$。

考虑以 $\vec{i},\vec{x}$ 组成的平行四边形，面积为 y，经过变换 A 后面积变为 $\|A\|\cdot y$。

因此我们有如下等式：

$$
y = \frac{
    \begin{vmatrix}
    2&4\\0&2
    \end{vmatrix}
}{
    \begin{vmatrix}
    2&-1\\0&1
    \end{vmatrix}
}
$$