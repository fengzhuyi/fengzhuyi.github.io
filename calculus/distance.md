---
title: 路程
mathjax: true
---

假设有一辆车，车的起步速度 v 和时间 t 的关系如下：

$$
v(t)=2t
$$

那么车从 0 到 1 秒走过的路程是 1。

下面讲解计算过程。

## 微元与积分

我们知道车的路程等于平均速度乘以时间。

假设车的平均速度等于 1 秒时的瞬间速度 2。

此时根据平均速度乘以时间得到结果为 `2`，和正确答案相差很远。

那如果将 0 到 1 秒分成多个时段分别计算呢？

假设每个时段间隔为 $dt=0.5$，并把时段末的速度作为平均速度，则有：

$$
L = 0.5\times1+0.5\times2=1.5
$$

我们发现离正确答案更近了。

如果时间间隔 $dt$ 不断变小，发现各时间段的路程相加越来越接近正确答案。

这里的计算涉及到了两个步骤：

- 微元：将时间段不断缩小
- 积分：将各时间段的路程相加

## 曲线与面积

仔细观察会发现：

- 速度在坐标系上表示一条曲线
- 路程是曲线下的面积