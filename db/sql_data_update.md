---
title: SQL 数据更新
---

数据更新包括插入、修改和删除操作。

## 插入数据

SQL 使用 INSERT 语句插入数据。

如插入一条数据到 student 表中：

```sql
INSERT INTO student(id, name, sex, age, dept)
VALUES('20230214', '张三', '男', '18', 'math');
```

若不指出属性名，则表明新元组要在表的所有属性列上都指定值，属性列的次序与 CREATE TABLE 中的次序相同。

SQL 允许插入子查询结果。

如对每个系，求学生的平均年龄，并把结果存入数据库：

```sql
/* 先建表 */
CREATE TABLE dept_age (
    dept CHAR(15),
    avg_age SMALLINT
);

/* 插入数据 */
INSERT INTO dept_age(dept, avg_age)
SELECT dept, AVG(age) FROM student
GROUP BY dept;
```

## 修改数据

SQL 使用 UPDATE 语句修改数据。

如修改学生的年龄：

```sql
UPDATE student 
SET age = 22
WHERE id = '2016520';
```

SQL 支持同时修改多个元组的值。

如将所有学生的年龄增加 1 岁：

```sql
UPDATE student
SET age = age + 1;
```

子查询也可以嵌套在 UPDATE 语句中。

如将数学系全体学生的成绩置零：

```sql
UPDATE course
SET grade = 0
WHERE sid IN (
    SELECT sid FROM student
    WHERE dept = 'math'
);
```

## 删除数据

SQL 使用 DELETE 子句删除数据。

如删除某个学生记录：

```sql
DELETE FROM student
WHERE id = '2016520';
```

删除所有学生选课记录：

```sql
DELETE FROM course;
```

SQL 可执行带子查询的删除语句。

如删除数学系所有学生的选课记录：

```sql
DELETE FROM course
WHERE sid IN (
    SELECT sid FROM student
    WHERE dept = 'math'
);
```
