---
title: markdown 写作样式
---

---

# 一级标题

## 二级标题

### 三级标题

#### 四级标题

---

## 段落与文本

段落中允许不同样式的字体出现，包括：

- *斜体字* 的格式为 `*斜体字*`
- **粗体字** 的格式为 `**粗体字**`
- ~~删除线~~ 的格式为 `~~删除线~~` 
- <u>下划线</u> 的格式为 `<u>下划线</u>`

段落支持链接，例如链接到[我的首页](https://www.professordeng.com)，语法如下：

```markdown
[我的首页](https://www.professordeng.com)
```

段落支持脚注，如下面的一句话，点击句末的脚注，会跳转到文章末尾的引用。

不在沉默中爆发，就在沉默中灭亡。[^luxun]

如果想高亮某一句话，在段首加上 `>` 即可。 

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

## 图片

通过语法 `![名称](链接)` 插入图片，样例如下

![picture](img/big.jpg)

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

## 参考

[^luxun]: 鲁迅《纪念刘和珍君》