---
title: 网站样例
mermaid: true
mathjax: true
---

# 大标题

## 二级标题

### 三级标题

#### 四级标题

---

## 段落

段落中允许不同样式的字体出现，例如 *斜体字* 、**粗体字** 、~~删除~~ 和 <u>下划线</u>。

如果你有疑问，可以 [baidu](http://www.baidu.com/) 一下。

不在沉默中爆发，就在沉默中灭亡。[^luxun]

> 想要和得到，中间还有两个字，那就是要做到，只有做到了才能得到。

---

## 代码

如下是 C 代码样例

```c
int main() {
	printf("hello world!");
	return 1;
}
```

如下是超长代码样例

```
My father used to say, whatever you do, do it a hundred percent, when you work, work, when you laugh, laugh, when you eat, eat like it is your last meal.
```

---

## 表格

简易表格如下

|       | mathematics | English | Chinese | Politics |
| ----- | ----------- | ------- | ------- | -------- |
| David | 80          | 80      | 50      | 100      |
| James | 70          | 80      | 90      | 100      |
| Me    | 100         | 90      | 100     | 100      |

超长表格如下

|       | mathematics | English | Chinese | Politics | Japanese | python | basketball | javascript |
| ----- | ----------- | ------- | ------- | -------- | -------- | ------ | ---------- | ---------- |
| David | 80          | 80      | 50      | 100      | 98       | 100    | 99         | 1          |
| James | 70          | 80      | 90      | 100      | 12       | 90     | 88         | 2          |
| Me    | 100         | 90      | 100     | 100      | 120      | 50     | 77         | 3          |

不过一般不使用超长表格，影响阅读体验。

---

## 数学公式

数学公式由 [MathJax](https://www.mathjax.org/) 提供支持，样例如下

圆的周长 $c$ 和半径 $r$ 的关系:

$$
c=2 \pi r
$$

---

## 流程图

流程图由 [Mermaid](https://mermaid.js.org/) 提供支持，样例如下

<div class="mermaid">
graph LR
    A --- B
    B-->C[fa:fa-ban forbidden]
    B-->D(fa:fa-spinner);
</div>

---

## 图片

通过语法 `![名称](链接)` 插入图片，样例如下

![picture](img/big.jpg)

---

## Youtube

获取 YouTube 视频的 id，填入 src 的链接中

``` html
<iframe class="video" src="链接" allowfullscreen></iframe>
```

样例如下

<iframe class="video" src="https://www.youtube.com/embed/-wFsYY71wyk" allowfullscreen></iframe>

---

## 列表

无序列表如下

- 数学
- 英语

有序列表如下

1. 打开冰箱
2. 装入大象

待办无序列表如下

- [x] 吃饭
- [ ] 睡觉

待办有序列表如下

1. [x] 洗澡
2. [ ] 化妆

## B 站

获取 B 站视频的 bvid，填入 src 的链接中

```html
<iframe class="video" src="链接" allowfullscreen> </iframe>
```

样例如下

<iframe class="video" src="//player.bilibili.com/player.html?bvid=BV1rK4y177YB" allowfullscreen> </iframe>

## Video

获取 mp4 链接，填入 src 的链接中

```html
<video src="链接" controls controlsList="nodownload"></video>
```

样例如下

<video src="https://cdn-video.xinpianchang.com/5b7fc02a84108.mp4" controls controlsList="nodownload"></video>

## 参考

[^luxun]: 鲁迅《纪念刘和珍君》