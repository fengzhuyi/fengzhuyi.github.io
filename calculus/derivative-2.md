---
title: 求导
mathjax: true
---

导数描述了某个点附近的最佳近似，因此微小变化量是导数的本质。

让我们先从幂函数的导数说起吧。

$$
\frac{dx^n}{dx}=nx^{n-1}
$$

## 面积增量

$A=x^2$ 表示边长为 $x$ 的面积。

$x$ 的微小增量 $dx$ 会引起 $A$ 的微小增量 $dA$。

$A$ 的几何意义是正方形，其面积增量为：

$$
dA = xdx + xdx + (dx)^2
$$

因此对应的导数为：

$$
\frac{dA}{dx} = 2x
$$

## 体积增量

$V=x^2$ 表示边长为 $x$ 的体积。

$V$ 的几何意义是正方体，其面积增量为：

$$
dV=3x^2dx + (\cdots)(dx)^2
$$

因此对应的导数为：

$$
\frac{dV}{dx}=3x^2
$$

对于大于 3 的自然数，其推理规则类似。

## 幂函数导数

从面积增量到体积增量，我们能推到出

$$
\frac{d(x^n)}{dx}=nx^{n-1}
$$

## 反函数

尝试从几何角度解读 $1/x$ 的导数。

$1/x$ 的图像可以解读为面积为 1 的矩形。

$$
x\cdot \frac1x=1
$$

此时给 x 一个微小的底边增量 $dx$，则有：

$$
-\frac1x dx= (x+d(\frac1x))d(\frac1x)
$$

左边表示增加的面积，右边表示减少的面积，左边的负号表示将`增加`变为`减少`。

化简即可得到：

$$
\frac{d(1/x)}{dx} = -(1/x^2)-\frac{d(1/x)}{x}\cdot\frac{d(1/x)}{dx}
$$

由于 $d(1/x)$ 是趋于 0 的，而 $x$ 是定值，得：

$$
\frac{d(1/x)}{dx} = -x^{-2}
$$

## 根号

来求一下 $\sqrt{x}$ 的导数，$\sqrt{x}$ 和 $x$ 关系如下：

$$
\sqrt{x}\cdot\sqrt{x}=x
$$

则给 x 一个微小的面积增量 $dx$，则有：

$$
dx=2\sqrt{x}d\sqrt{x}+d\sqrt{x}\cdot d\sqrt{x}
$$

化简可得：

$$
\frac{d\sqrt{x}}{dx}=\frac1{2\sqrt{x}}+\frac{d\sqrt{x}}{2\sqrt{x}}\cdot\frac{d\sqrt{x}}{dx}
$$

由于 $d\sqrt{x}$ 是趋于 0 的，而 $\sqrt{x}$ 是定值，得：

$$
\frac{d\sqrt{x}}{dx}=\frac1{2\sqrt{x}}
$$

## 正弦函数

三角函数是单位圆中 $\theta$ 与其他边的关系函数。

对于一个微小的角度增量 $\theta$，微观角度下是条直线，根据三角形相似有：

$$
\frac{d(\sin\theta)}{d\theta}=\frac{\cos\theta}1
$$

你也可以利用同样的方法求 $\cos\theta$ 的导数。