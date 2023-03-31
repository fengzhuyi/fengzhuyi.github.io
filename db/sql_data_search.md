---
title: SQL 数据查询
---

SQL 提供了 SELECT 语句进行数据查询。

## 单表查询

查询指定列属于投影运算，语法如下：

```sql
SELECT col_name FROM table_name; 
```

若想消除重复的元组，可以用 DISTINCT 关键词：

```sql
SELECT DISTINCT col_name FROM table_name;
```

查询满足条件的元组可通过 WHERE 子句实现：

```sql
SELECT col_name FROM table_name WHERE age < 20;
```

常用的查询条件包括：

- 运算符：如 =, >, <
- 确定范围：如 BETWEEN AND
- 确定集合：IN, NOT IN
- 字符匹配：LIKE, NOT LIKE
- 空值：IS NULL, IS NOT NULL
- 逻辑运算：AND, OR, NOT

可以用 ORDER BY 子句对查询结果进行降序（DESC）排列：

```sql
SELECT col_name FROM table_name
WHERE grade > 60
ORDER BY grade DESC;
```

为了方便检索，SQL 提供了许多聚集函数，包括：

```sql
COUNT(*) /* 统计元组个数 */
COUNT(DISTINCT col_name) /* 某列中不同的值的数量 */
SUM(col_name) /* 求某列的和 */
AVG(col_name) /* 求某列的平均数 */
MAX(col_name) /* 求某列的最大值 */
MIN(col_name) /* 求某列的最小值 */
```

使用样例如下：

```sql
SELECT COUNT(*) FROM table_name;
```

可以使用 GROUP BY 子句将查询结果按某个属性分组，值相同的为一组。

如性别相同为一组：

```sql
SELECT col_name FROM table_name
GROUP BY sex;
```

## 多表查询

多表查询也称连接查询。

SQL 用 WHERE 来连接两个表。

若有 student 表和 course 表，查询某学生的所有课程操作如下：

```sql
SELECT student.*, course.*
FROM student, course
WHERE student.id = course.sid;
```

连接操作包括自身连接，如查询每门课的先修课：

```sql
SELECT FIRST.id, SECOND pid
FROM course FIRST, course SECOND
WHERE FIRST.pid = SECOND.id;
```

其中 FIRST 和 SECOND 是别名。

连接操作包括外连接，如左连接：

```sql
SELECT student.id, student.name course.id, course.grade
FROM student LEFT OUTER JOIN course ON (student.id = course.sid);
```

其中 ON 用于生成临时表。作为对比，WHERE 会在 ON 生成的临时表上面起作用。

SQL 支持两张表以上的连接操作。

student 和 course 是多对多的关系，我们可以拆一个 sc 表来表示两个实体间的关系。

则涉及三个表的查询样例如下：

```sql
SELECT student.name, course.name, course.grade
FROM student, sc, course
WHERE student.id = sc.sid AND sc.cid = course.id;
```

## 嵌套查询

一个 SELECT-FROM-WHERE 语句称为一个查询块。

嵌套查询（nested query）指将一个查询块钱套在另一个查询块的 WHERE 子句的条件中。例如：

```sql
SELECT name FROM student
WHERE id IN (
    SELECT id FROM sc 
    WHERE cid = '2'
);
```

SQL 允许多层查询。

注意，子查询的 SELECT 语句中`不能`使用 ORDER BY 子句，ORDER BY 子句只能对最终查询结果排序。

嵌套查询中，子查询的结果通常是一个集合，所以 IN 是嵌套查询中最常用的谓词。

如查询`张三`所读的院系的所有学生：

```sql
SELECT id name, dept FROM student
WHERE dept IN (
    SELECT dept FROM student
    WHERE name = '张三'
);
```

例子中子查询的查询条件不依赖父查询，称为`不相关子查询`。

我们可以利用自身连接来实现相同的功能：

```sql
SELECT S1.id S1.name, S1.dept
FROM student S1, student S2
WHERE S1.dept = S2.dept AND S2.name = '张三';
```

可见实现同一个查询请求可以有多种方法，但不同方法的执行效率会有差异。

有些嵌套查询可以用连接运算替代，有些是不能替代的。

`相关子查询`指子查询的查询条件依赖于父查询。

如找出每个学生超过他自己选修课程平均成绩的课程号：

```sql
SELECT sid, id FROM course C1
WHERE grade >= (
    SELECT AVG(grade) FROM course C2
    WHERE C1.sid = C2.sid;
);
```

子查询返回单值时可以直接使用 `>=`，但返回多值时要用 ANY 或 ALL 谓语修饰符。

如查询数学系中比计算机系所有学生年龄都小的学生：

```sql
SELECT name, age FROM student
WHERE age < ALL(
    SELECT age FROM student
    WHERE dept = 'cs'
) AND dept = 'math';
```

本查询可以用聚集函数来实现：

```sql
SELECT name, age FROM student
WHERE age < (
    SELECT MAX(age) FROM
    WHERE dept = 'cs'
) AND dept = 'math';
```

事实上，用聚集函数实现子查询通常比直接用 ANY 或 ALL 查询效率要高。

SQL 提供 EXISTS 谓词，用于判断是否存在数据。

如查询所有选修了 1 号课程的学生姓名。

```sql
SELECT name FROM student
WHERE EXISTS (
    SELECT * FROM course
    WHERE course.pid = student.id AND course.id = '1'
);
```

若内层查询结果非空，则外层的 WHERE 子句返回真值。

由 EXISTS 引出的子查询，其目标列表达式通常都用 `*`，因为带 EXISTS 的子查询只返回真值或假值，给出列名无实际意义。

与 EXISTS 谓词相对应的是 NOT EXISTS 谓词。

## 集合查询

SELECT 语句的查询结果是元组的集合，所以多个 SELECT 语句的结果可进行集合操作。

集合操作主要包括并操作 UNION、交操作 INTERSECT 和差操作 EXCEPT。

如查询数学系的学生及年龄大于 19 岁的学生：

```sql
SELECT * FROM student WHERE dept = 'cs'
UNION
SELECT * FROM student WHERE age > 19;
```

## 基于派生表的查询

子查询不仅可以出现在 WHERE 子句中，还可以出现在 FROM 子句中，这时子查询生成的临时派生表（derived table）成为主查询的查询对象。

如查询所有选修了 1 号课程的学生姓名：

```sql
SELECT name
FROM student, (SELECT pid FROM course WHERE id = '1') AS C
WHERE student.id = C.pid;
```

通过 FROM 子句生成派生表时，必须为派生关系指定一个别名。
