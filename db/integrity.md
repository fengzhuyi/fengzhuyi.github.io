---
title: 数据库的完整性
---

数据库的完整性（integrity）指数据能正确反映现实世界。如人的年龄不能出现负数。

## 数据库管理系统的职责

要保证数据库的完整性，数据库管理系统需要实现如下功能

- 定义约束条件
- 检查操作是否符合约束条件
- 拒绝不符合约束条件的操作

## 实体完整性

关系模型的实体完整性在建表时用 PRIMARY KEY 定义。如：

```sql
CREATE TABLE person
(
    id CHAR(9) PRIMARY KEY,
    name CHAR(20) NOT NULL,
    sex CHAR(2)
);
```

定义了关系的主键后，每当进行插入或对主键进行更新时，RDBMS 会自动进行检查，包括：

- 主键必须唯一，否则拒绝操作。
- 主键必须不存在空值，否则拒绝操作。

## 参照完整性

关系模型的实体完整性在建表时用 FOREIGN KEY 定义。如：

```sql
CREATE TABLE order
(
    id INT PRIMARY KEY,
    no INT NOT NULL,
    pid INT FOREIGN KEY REFERENCES person(id)
);
```

参照完整性将 order 表和 person 表的相应元组联系起来了。

定义了关系的外键后，每当进行增、删、改操作时，RDBMS 会自动进行检查，不合理的情况包括：

- 增加 order 记录，其 pid 在 person 中不存在
- 修改 order 记录，导致其 pid 在 person 中不存在
- 删除 person 记录，造成 order 的外键失效
- 修改 person 记录，造成 order 的外键失效

当出现不合理情况时，系统可采取以下策略：

- 拒绝执行（默认策略）
- 级联操作（删除所有异常元组）
- 设置为空值（一般不允许为空）

## 用户定义的完整性

数据库中的数据定义必须满足用户的要求，包括数据的约束条件。

对属性的约束包括：

- 列值非空（NOT NULL）
- 列值唯一（UNIQUE）
- 检查列值是否满足约束条件（CHECK）

样例如下：

```sql
CREATE TABLE person 
(
    id CHAR(9) PRIMARY KEY,
    name CHAR(20) NOT NULL,
    wechat CHAR(20) UNIQUE,
    sex CHAR(2) CHECK(sex IN ('男','女'))
);
```

元组内不同属性间可以添加条件约束。

如当性别为男时，名字不能以 Ms. 打头。

```sql
CREATE TABLE person
(
    id CHAR(9) PRIMARY KEY,
    name CHAR(20) NOT NULL,
    sex CHAR(2),
    CHECK(sex='女' OR name NOT LIKE 'Ms.%')
);
```

若插入的数据不满足约束条件，RDBMS 拒绝执行。

## 约束命名

SQL 用 CONSTRAINT 对约束条件命名。

```sql
CREATE TABLE person
(
    id CHAR(9) PRIMARY KEY,
    age NUMERIC(3)
    CONSTRAINT c1 CHECK(age < 30),
    name CHAR(20)
);
```

删除约束条件的语句是：

```sql
ALTER TABLE person
DROP CONSTRAINT c1;
```

## 触发器

触发器（trigger）和约束类似，但更灵活，可以实施更为复杂的检查和操作。

触发器创建有四要素

- 监视地点（table）
- 监视事件（update、insert、delete）
- 触发事件（before、after）
- 触发事件（update、insert、delete）

触发器定义格式如下：

```sql
CREATE TRIGGER trigger_name
BEFORE INSERT ON table_name
FOR EACH ROW
BEGIN
    event;
END;
```

删除触发器的语法如下：

```sql
DROP TRIGGER trigger_name ON table_name;
```

谨慎使用触发器，因为触发器会影响系统性能。