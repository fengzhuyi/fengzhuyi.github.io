---
title: 行列式
mathjax: true
---

> 行列式（Determinant）是伸缩因子。

阅读本文前，需要先了解[线性变换](matrix)。

## 单位元

在平面直角坐标系中，以 ($\vec{i}$, $\vec{j}$) 为基。

将 $\vec{i}$ 和 $\vec{j}$ 围成的面积作为单位元。

所有坐标都用 $\vec{i}$ 和 $\vec{j}$ 线性表示。

## 伸缩

对 $\vec{i}$ 和 $\vec{j}$ 进行伸缩变换，变换矩阵如下

$$
A = \begin{bmatrix}3&0\\0&2\end{bmatrix}
$$

变换后单位元的面积为变为原来的 6 倍。

矩阵 $A$ 对应的行列式 $D$ 为：

$$
D = \begin{vmatrix}3&0\\0&2\end{vmatrix} = 6
$$

## 剪切

对 $\vec{i}$ 和 $\vec{j}$ 进行剪切变换，变换矩阵如下

$$
A = \begin{bmatrix}1&1\\0&1\end{bmatrix}
$$

变换后单位元的面积不变。

矩阵 $A$ 对应的行列式 $D$ 为：

$$
D = \begin{vmatrix}1&1\\0&1\end{vmatrix} = 1
$$

## 降维

考虑如下变换矩阵：

$$
A = \begin{bmatrix}4&2\\2&1\end{bmatrix}
$$

变换后 $\vec{i}$ 和 $\vec{j}$ 共线，单位元面积为 0，此时整个平面被压缩成一条线。

矩阵 $A$ 对应的行列式 $D$ 为：

$$
D = \begin{vmatrix}4&2\\2&1\end{vmatrix} = 0
$$

此时矩阵的列线性相关。

## 翻转

行列式可以是负数，如：

$$
A = \begin{bmatrix}0&1\\1&0\end{bmatrix} = -1
$$

变换后 $\vec{i}$ 和 $\vec{j}$ 的相对位置发生了变换，负号可理解为平面发生了翻转。

行列式的绝对值仍然代表单位元的伸缩比例。

在三维空间中，可以用右手定则来判断是否发生了空间翻转。

## 复合

如果理解了行列式是伸缩因子，那么下列式子很容易理解：

$$
\det(M_1 M_2) = \det{(M_1)}\cdot\det{(M_2)}
$$

## 体积

若某个抽象的东西满足体积应有的一切性质，可将其称为体积。

体积函数 $V$ 必须满足三个性质：

1. $V(k\cdot \vec{v_i}) = k\cdot V(\vec{v_i})$
2. $V(\vec{v_i} + \vec{w_i}) = V(\vec{v_i}) + V(\vec{w_i})$
3. $i\neq j,\ \vec{v_i} = \vec{v_j}\to V(\vec{v_i}, \vec{v_j}) = 0$

根据上述性质可推出：交换两个向量的位置得到的新体积是原体积的相反数。

行列式的定义正好满足体积函数的性质：

$$
\det(A) = \sum_{\sigma \in S_n} \text{sgn}(\sigma) \prod_{i=1}^n a_{i,\sigma(i)}
$$

## 二维行列式

下面给出二维空间的行列式定义的直观证明。

设二维向量空间的基为 $(\vec{i}, \vec{j})$。

基围成的体积 $V(\vec{i}, \vec{j})=1$。

根据体积函数定义，任意两个向量 $\vec{v}$ 和 $\vec{w}$ 围成的体积为：

$$
\begin{align}
V(\vec{v}, \vec{w}) &= V(a\vec{i}+b\vec{j}, c\vec{i}+d\vec{j}) \\
        &= ad\cdot V(\vec{i}, \vec{j}) + bc\cdot V(\vec{j}, \vec{i}) \\
        &= (ad-bc)\cdot V(\vec{i}, \vec{j}) \\
        &= ad - bc
\end{align}
$$

$V(\vec{j},\vec{i})$ 的变换对应行列式定义的 $\text{sgn}(\sigma)$。

## 拉普拉斯展开

三维空间的行列式计算可以类比二维行列式的计算：

$$
\begin{align}
V(\vec{u}, \vec{v}, \vec{w}) 
        &= V(a\vec{i}+b\vec{j}+c\vec{k}, \vec{v}, \vec{w}) \\
        &= a V_{ivw}+b V_{jvw}+c V_{kvw} \\
        &= a V_{ivw}-b V_{vjw}+c V_{vwk}
\end{align}
$$

其中 $V_{ivw} = V(\vec{i}, \vec{v}, \vec{w})$。

$V_{ivw}$ 等于 $\vec{v}$ 和 $\vec{w}$ 在 $y\circ z$ 平面上的投影面积。

设 $\vec{v}$ 在 y 和 z 轴的分量和为 $d\vec{j}+e\vec{k}$。

设 $\vec{w}$ 在 y 和 z 轴的分量和为 $f\vec{j}+g\vec{k}$。

则投影面积可表示为：

$$
A = \begin{vmatrix}d&f\\e&g\end{vmatrix}
$$

同理，$V_{vjw}$ 和 $V_{vwk}$ 都可以用一个二维行列式表示。

因此，三维行列式的计算过程如下：

$$
\begin{vmatrix} a & d & g \\ b & e & h \\ c & f & i \end{vmatrix} =
  a \cdot \begin{vmatrix} e & h \\ f & i \end{vmatrix} 
- b \cdot \begin{vmatrix} d & g \\ f & i \end{vmatrix} 
+ c \cdot \begin{vmatrix} d & g \\ e & h \end{vmatrix}
$$

这就是拉普拉斯展开的本质。