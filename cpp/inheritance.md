---
title: 继承
---

继承是一种面向对象编程的概念，它允许创建一个新类（称为派生类或子类），从已有的类（称为基类或父类）继承属性和方法。

C++ 中定义继承的语法格式如下：

```
class 派生类名 : 访问修饰符 基类名 {
public:
    派生类成员声明;
};
```

其中，派生类名是新创建的类的名称，访问修饰符可以是 public、protected 或 private，用于指定基类成员的访问权限。

例如，以下是一个基类 Shape 和其子类 Circle 的示例：

```cpp
class Shape {
protected:
    int x, y; // 基类成员变量
public:
    void setOrigin(int x, int y) { // 基类成员函数
        this->x = x;
        this->y = y;
    }
};

class Circle : public Shape { // 派生类 Circle 继承自 Shape
private:
    int radius; // 派生类成员变量
public:
    void setRadius(int radius) { // 派生类成员函数
        this->radius = radius;
    }
    double getArea() { // 派生类成员函数
        return 3.14 * radius * radius;
    }
};
```

在上面的示例中，派生类 Circle 继承自基类 Shape，通过 public 访问修饰符指定基类成员的访问权限。派生类 Circle 中定义了一个私有成员变量 radius 和两个公有成员函数 setRadius 和 getArea，其中 setRadius 设置半径，getArea 计算圆的面积。

可以通过以下方式创建 Circle 对象，并使用基类 Shape 中的函数设置其坐标：

```cpp
Circle c;
c.setOrigin(1, 2);
c.setRadius(3);
cout << "Circle area: " << c.getArea() << endl;
```

派生类可以访问基类的公有成员，但不能直接访问基类的私有成员，必须通过基类的公有成员函数来访问。