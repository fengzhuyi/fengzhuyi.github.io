---
title: 叉积
mathjax: true
---

向量 $\vec{u}$ 和向量 $\vec{v}$ 的叉积是一个向量。

## 二维向量叉积

叉积的大小是平行四边形的面积，面积用[行列式](/la/determinant)计算。

很显然，两个向量的夹角越小，其叉积越大。

叉积的方向符合右手定则。

## 矩阵表示

在三维空间中，求向量 $\vec{u}$ 和向量 $\vec{v}$ 的叉积如下：

$$
\vec{u}\times \vec{v} = 
\begin{vmatrix}
  \vec{i}&u_1&v_1\\
  \vec{j}&u_2&v_2\\
  \vec{k}&u_3&v_3
\end{vmatrix}
$$

本文讲讲为什么叉积能用该行列式表示。

## 体积

三维空间的行列式可表示体积。考虑以下函数

$$
f\left(
    \begin{bmatrix}
    x\\y\\z
    \end{bmatrix}
\right)
= \begin{vmatrix}
  x&u_1&v_1\\
  y&u_2&v_2\\
  z&u_3&v_3
\end{vmatrix}
= V
$$

这是个线性函数，输入是一个三维向量，输出是一个一维向量（标量）。

因此，我们可以用线性变换来表示，即三维到一维的投影。

$$
A\vec{w} = 
\begin{vmatrix}
  x&u_1&v_1\\
  y&u_2&v_2\\
  z&u_3&v_3
\end{vmatrix}
= V
$$

其中 A 是 $1\times 3$矩阵，则线性变换可用[点积](/la/dot-product)表示。

$$
\vec{p}\cdot\vec{w}
= \begin{vmatrix}
  x&u_1&v_1\\
  y&u_2&v_2\\
  z&u_3&v_3
\end{vmatrix}
= V
$$

根据待定系数法，就可求出 $\vec{p}$。

## 几何意义

$\vec{p}\cdot\vec{w}$ 相当于 $\vec{w}$ 在 $\vec{p}$ 上的投影长度与 $\vec{p}$ 的长度之积。

体积 $V$ 相当于 $\vec{w}$ 在法向量上的投影长度与底面积之积。

由于 $\vec{w}$ 是任意的，因此 $\vec{p}$ 必然垂直于 $\vec{u}$ 和 $\vec{v}$，且长度与这两个向量张成的平行四边形面积相同。

也就是说 $\vec{p}$ 就是 $\vec{u}$ 和 $\vec{v}$ 的叉积。

这就是叉积的计算过程与几何解释有关联的根本原因。

## 替换技巧

将 $\vec{w}$ 用 $(\vec{i}, \vec{j}, \vec{k})$ 替代，即可快速求出 $\vec{p}$ 用基坐标表示的表达式。

这只不过是利用了几何意义的结论罢了。