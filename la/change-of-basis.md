---
title: 基变换
mathjax: true
---

在平面坐标系中，我们一般会采用 $(\vec{i},\vec{j})$ 作为基向量。

如向量 $(3, 2)$ 可表示为：

$$
\begin{bmatrix}
3\\2
\end{bmatrix} =
3\vec{i} + 2\vec{j}
$$

但可以采用不同的基向量来表示一个平面：

$$
\vec{a}=\begin{bmatrix}2\\1\end{bmatrix},\ 
\vec{b}=\begin{bmatrix}-1\\1\end{bmatrix}
$$

此时向量 $(3,2)$ 在基向量 $(\vec{a},\vec{b})$ 上的表达为：

$$
\begin{bmatrix}
3\\2
\end{bmatrix} =
\frac53\vec{a} + \frac13\vec{b}
$$

对上式做一些调整可得：

$$
\begin{bmatrix}
3\\2
\end{bmatrix} = 
\begin{bmatrix}\vec{a}&\vec{b}\end{bmatrix}
\begin{bmatrix}
5/3\\1/3
\end{bmatrix}
$$

其中 $\begin{bmatrix}\vec{a}&\vec{b}\end{bmatrix}$ 为基变换。

含义是将 $(\vec{a},\vec{b})$ 所表示的向量转换为 $(\vec{i},\vec{j})$ 表示。

## 旋转

在二维平面中，以 $(\vec{i},\vec{j})$ 为基向量，则旋转 $90^{\circ}$ 的变换矩阵为：

$$
A=\begin{bmatrix}
0&-1\\
1&0
\end{bmatrix}
$$

若以 $(\vec{a},\vec{b})$ 为基向量，则其旋转 $90^{\circ}$ 的过程可分解为：

```
基变换 --> 旋转 --> 基变换
```

用矩阵表示为：

$$
\begin{bmatrix}
2&-1\\
1&1
\end{bmatrix}^{-1}
\begin{bmatrix}
0&-1\\
1&0
\end{bmatrix}
\begin{bmatrix}
2&-1\\
1&1
\end{bmatrix}
$$

即 $Q^{-1}AQ=B$，也就是说 B 和 A 的作用相同，但应用在不同的基向量上。

我们称 A 与 B 相似