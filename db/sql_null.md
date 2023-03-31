---
title: SQL 空值
---

空值有三个含义：不知道、不存在、无意义。

SQL 允许某些属性在一定情况下取空值，如：

- 不知道具体值，如年龄、性别
- 不应该有值，如缺考没有成绩
- 涉及隐私不方便填写，如手机

## 空值的产生

插入学生记录时，成绩为空：

```sql
INSERT INTO course(id, sid, grade)
VALUES('1', '2016520', NULL);
```

插入记录时学生还没有考试成绩。

## 空值的判断

从 student 表中寻找漏填信息的学生记录：

```sql
SELECT * FROM student
WHERE name IS NULL OR sex IS NULL;
```

## 空值的约束条件

有 NOT NULL 约束的属性不能取空值。

有 UNIQUE 限制的属性不能取空值。

## 空值的运算

空值与另一个值的算术运算的结果为空值。

空值与另一个值的比较运算的结果为 UNKNOWN。有了 UNKNOWN 后，传统的逻辑运算中二值 (TRUE, FALSE) 逻辑就扩展成了三值逻辑。

三值运算的真值表如下：

| A | B | A ∨ B | A ∧ B | ¬ A |
|---|---|-------|-------|-----|
| T | T | T     | T     | F   |
| T | U | T     | U     | F   |
| T | F | T     | F     | F   |
| U | T | T     | U     | U   |
| U | U | U     | U     | U   |
| U | F | U     | F     | U   |
| F | T | T     | F     | T   |
| F | U | U     | F     | T   |
| F | F | F     | F     | T   |