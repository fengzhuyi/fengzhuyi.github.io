---
title: 多态
---

C++ 中的多态（Polymorphism）指的是同一个类的不同对象，调用同一个方法时可以产生不同的行为。

C++ 通过虚函数实现多态。

虚函数是一种在基类中声明的函数，它在派生类中被`重写`，使得派生类能够用自己的方法实现基类的函数。virtual 关键词用于表示该函数是可以被重写的。在调用虚函数时，编译器会根据实际对象的类型来选择调用哪个函数，从而实现多态。

```cpp
#include <iostream>

using namespace std;

class Shape {
   protected:
      int width, height;

   public:
      Shape( int a=0, int b=0) {
         width = a;
         height = b;
      }

      virtual int area() {
         cout << "Parent class area :" <<endl;
         return 0;
      }
};

class Rectangle: public Shape {
   public:
      Rectangle( int a=0, int b=0):Shape(a, b) { }

      int area () {
         cout << "Rectangle class area :" <<endl;
         return (width * height);
      }
};

class Triangle: public Shape{
   public:
      Triangle( int a=0, int b=0):Shape(a, b) { }

      int area () {
         cout << "Triangle class area :" <<endl;
         return (width * height / 2);
      }
};

int main() {
   Shape *shape;
   Rectangle rec(10,7);
   Triangle  tri(10,5);

   // 存储矩形的地址
   shape = &rec;

   // 调用矩形的求面积函数 area
   shape->area();

   // 存储三角形的地址
   shape = &tri;

   // 调用三角形的求面积函数 area
   shape->area();

   return 0;
}
```

在上述代码中，Shape 是一个基类，其中包含一个虚函数 area()，Rectangle 和 Triangle 是 Shape 的两个派生类，它们都重写了 area() 函数。

在主函数中，首先声明了一个 Shape 类型的指针 shape，然后将其指向 Rectangle 对象，调用了 area() 函数，编译器会根据实际对象的类型来选择调用 Rectangle 类的 area() 函数，输出相应的结果。然后将 shape 指针指向 Triangle 对象，再次调用 area() 函数，编译器会根据实际对象的类型来选择调用 Triangle 类的 area() 函数，输出相应的结果。