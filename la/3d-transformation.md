---
title: 三维空间的线性变换
mathjax: true
---

三维空间的线性变换对机器人学和计算机图形学都很重要。

矩阵用来表示线性变换，因此三维矩阵可用来表示三维空间的线性变换。

## 旋转

我们用 $\vec{i}$、$\vec{j}$ 和 $\vec{k}$ 来表示三维空间的基向量。

考虑沿着 y 轴旋转 $90^{\circ}$ 的变换，变换后的基向量分别如下

$$
\vec{i} \to \begin{bmatrix}0\\0\\-1\end{bmatrix},\ 
\vec{j} \to \begin{bmatrix}0\\1\\0\end{bmatrix},\ 
\vec{k} \to \begin{bmatrix}1\\0\\0\end{bmatrix}
$$

这三组坐标就成了描述这一旋转变换的矩阵的三列

$$
A = \begin{bmatrix}0&0&1\\0&1&0\\-1&0&0\end{bmatrix}
$$

因此 $A\vec{v}$ 表示变换后的向量。

可以发现推理过程与二维几乎相同。

## 复合变换

三维空间中的旋转很难直接表述，但由于[矩阵乘法](matrix-multiplication)满足结合律，我们可以将变换拆分成多个简单变换的复合。