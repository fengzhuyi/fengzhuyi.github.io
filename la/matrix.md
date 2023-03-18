---
title: 矩阵与线性变换
mathjax: true
---

> 上一章：[线性组合](linear-combination)

线性变换（Linear Transformation）是将向量作为输入和输出的一类函数。

## 本质

考虑 $\vec{v} = -1\cdot \vec{i} + 2\cdot\vec{j}$，分别对 $\vec{i}$ 和 $\vec{j}$ 进行变换：

$$
\vec{i} = \begin{bmatrix}1\\-2\end{bmatrix},\ \vec{j} = \begin{bmatrix}3\\0\end{bmatrix}
$$

$\vec{v}$ 以 $\vec{i}$ 和 $\vec{j}$ 为基，则 $\vec{v}$ 的变换如下：

$$
\vec{v} = -1\cdot\begin{bmatrix}1\\-2\end{bmatrix} + 2\cdot\begin{bmatrix}3\\0\end{bmatrix}=\begin{bmatrix}5\\2\end{bmatrix}
$$

对基 $\vec{i}$ 和 $\vec{j}$ 施加变换，$\vec{v}$ 也随之变换，该过程称为线性变换。

## 矩阵

将 $\vec{v}$ 抽象成未知向量 $x\cdot\vec{i} + y\cdot\vec{j}$，变换过程可描述为：

$$
\vec{v} = x\cdot\begin{bmatrix}1\\-2\end{bmatrix} + 2\cdot\begin{bmatrix}3\\0\end{bmatrix}
=\begin{bmatrix}1&3\\-2&0\end{bmatrix}\begin{bmatrix}x\\y\end{bmatrix} = A\vec{v}
$$

通过 $A\vec{v}$ 运算，可以求出变换后的 $\vec{v}$ 的坐标。

称 $A$ 为 $2\times 2$ 矩阵，矩阵的列是变换后的基向量。

## 旋转

对基向量逆时针旋转 $90^{\circ}$，坐标变为：

$$
\vec{i} = \begin{bmatrix}0\\1\end{bmatrix},\ \vec{j} = \begin{bmatrix}-1\\0\end{bmatrix}
$$

向量 $\vec{v}$ 随之旋转 $90^{\circ}$，计算如下： 

$$
\vec{v} = \begin{bmatrix}0&-1\\1&0\end{bmatrix}\begin{bmatrix}x\\y\end{bmatrix}
$$

## 剪切

$\vec{i}$ 保持不变，$\vec{j}$ 变换如下：

$$
\vec{j} = \begin{bmatrix}1\\1\end{bmatrix}
$$

则向量 $\vec{v}$ 的变换如下

$$
\vec{v} = \begin{bmatrix}1&1\\0&1\end{bmatrix}\begin{bmatrix}x\\y\end{bmatrix}
$$

剪切（Shear）过程像是把叠好的扑克牌往一边推，形成平行四边形。

## 总结

线性变换计算直观，通过 $A\vec{v}$ 即可求出所有变换后的向量。

其中 $A$ 是 $2\times 2$ 矩阵，矩阵的列是变换后的基向量。

> 下一章：[矩阵乘法](/la/matrix-multiplication)