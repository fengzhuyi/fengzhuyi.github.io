---
title: SQL 数据定义
---

关系数据库的基本对象包括模式、表、视图和索引。

数据库层次关系如下：

```
数据库 --> 模式 --> 表、视图、索引
```

## 1. 模式的定义与删除

模式是数据库的命名空间。

定义模式的语法如下：

```sql
CREATE SCHEMA schema_name AUTHORIZATION user_name;
```

之后可以在模式下定义表、视图和索引。

删除模式的语法如下：

```sql
DROP SCHEMA schema_name RESTRICT;
```

若模式下有数据库对象（如表、视图等），则拒绝执行该语句。

如果想删除模式及模式下的对象，可采用如下语句：

```sql
DROP SCHEMA schema_name CASCADE;
```

### 2. 表的定义、删除与更新

表的定义语法如下：

```sql
CREATE TABLE table_name
(
    col_name data_type constraint, 
    col_name data_type constraint, 
    col_name data_type constraint, 
    col_name data_type constraint
);
```

数据类型用于表示属性的域，属性的约束是可选的。

如创建一个学生表：

```sql
CREATE TABLE Student
(
    id CHAR(9) PRIMARY KEY, 
    name CHAR(20) UNIQUE, 
    sex CHAR(2), 
    age SMALLINT 
);
```

添加属性的语法如下：

```sql
ALTER TABLE table_name 
ADD col_name data_type;
```

删除属性的语法如下：

```sql
ALTER TABLE table_name
DROP COLUMN column_name;
```

删除表的语法如下：

```sql
DROP TABLE table_name
```

### 3. 索引的建立与删除

建立索引是加快查询速度的有效手段。

数据库索引有多种类型，包括顺序索引、B+ 树索引和散列（hash）索引等。

建立索引的语法如下：

```sql
CREATE INDEX index_name
ON table_name (col_name);
```

修改索引名字的语法如下：

```sql
ALTER  INDEX old_index_name
RENAME TO new_index_name;
```

如果数据增、删、改频繁，系统会花费许多时间来维护索引，可以考虑删除一些不必要的索引。

删除索引的语法如下：

```sql
DROP INDEX index_name;
```