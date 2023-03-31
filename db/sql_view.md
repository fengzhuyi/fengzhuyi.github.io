---
title: SQL 视图
---

视图是从基本表中导出的表，是一个虚表。

## 定义视图

建立数学系学生的视图：

```sql
CREATE VIEW math_student AS
SELECT id, name, age FROM student
WHERE dept='math'
WITH CHECK OPTION;
```

加上 WITH CHECK OPTION 后，对视图进行更新操作时，系统会自动加上 `dept = 'math'` 的条件。

删除视图的语句如下：

```sql
DROP VIEW math_student;
```

## 查询视图

视图的查询和基本表没啥区别。

如查询数学系中年龄小于 20 岁的学生：

```sql
SELECT id, age FROM math_student
WHERE age < 20;
```

## 视图的作用

- 仅展示用户需要的数据
- 对机密数据提供安全保护
- 适当利用视图能使逻辑更清晰
