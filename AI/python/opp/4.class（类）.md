类（class）是创建对象的模板。对象是类的实例，包含：

- **属性**（attribute）：对象保存的数据
- **方法**（method）：定义在类里的函数，用来操作这些数据

## 定义类

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def greet(self):
        return f"Hello, my name is {self.name}."

p = Person("Alice", 25)
print(p.name)      # Alice
print(p.age)       # 25
print(p.greet())   # Hello, my name is Alice.
```

- `class` 定义类，类名习惯用大驼峰（`Person`）
- `__init__` 是构造方法，创建实例时自动调用
- `self` 指向实例本身，是方法的第一个参数；调用时不用手动传
- `self.name = name` 创建实例属性
- 方法就是定义在类里的函数，第一个参数通常叫 `self`

### 类属性与实例属性

```python
class Dog:
    species = "Canis familiaris"  # 类属性，所有实例共享

    def __init__(self, name):
        self.name = name          # 实例属性，每个实例独立

a = Dog("A")
b = Dog("B")

print(a.species, b.species)  # Canis familiaris Canis familiaris
print(a.name, b.name)        # A B
```

类属性适合保存所有实例共用的常量或默认值；每个对象自己的数据应放在 `__init__` 里。

## 类方法与静态方法

```python
class Circle:
    def __init__(self, radius):
        self.radius = radius

    @classmethod
    def from_diameter(cls, diameter):
        return cls(diameter / 2)

    @staticmethod
    def area_formula():
        return "π * r²"

c = Circle.from_diameter(10)
print(c.radius)                # 5.0
print(Circle.area_formula())   # π * r²
```

- **实例方法**：第一个参数是 `self`，操作具体对象
- **类方法** `@classmethod`：第一个参数是 `cls`，常用于提供备选构造方法
- **静态方法** `@staticmethod`：没有 `self` / `cls`，只是放在类命名空间里的普通函数

## 继承

子类继承父类的属性和方法，可以复用代码并扩展功能：

```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age

    def greet(self):
        return f"Hi, I'm {self.name}."

class Student(Person):
    def __init__(self, name, age, school):
        super().__init__(name, age)  # 调用父类的构造方法
        self.school = school

    def greet(self):                 # 重写父类方法
        return f"Hi, I'm {self.name}, a student at {self.school}."

s = Student("Bob", 20, "Tsinghua")
print(s.name, s.age, s.school)  # Bob 20 Tsinghua
print(s.greet())                # Hi, I'm Bob, a student at Tsinghua.
```

类型判断：

```python
print(isinstance(s, Student))   # True
print(isinstance(s, Person))    # True，子类实例也是父类类型
print(issubclass(Student, Person))  # True
```

- `super()` 用来调用父类的方法，最常见的是 `super().__init__(...)`
- 子类定义同名方法会**覆盖**父类方法
- 支持多重继承 `class C(A, B)`，方法查找顺序由 MRO 决定，可以用 `C.__mro__` 查看

## 抽象类

抽象类定义一组接口，规定子类必须实现哪些方法：

```python
class Shape():
    @abstractmethod
    def area(self):
        pass

    @abstractmethod
    def perimeter(self):
        pass

class Rectangle(Shape):
    def __init__(self, width, height):
        self.width = width
        self.height = height

    def area(self):
        return self.width * self.height

    def perimeter(self):
        return 2 * (self.width + self.height)

r = Rectangle(3, 4)
print(r.area())       # 12
print(r.perimeter())  # 14
```

- 抽象类不能直接实例化，`Shape()` 会抛出 `TypeError`
- 子类必须实现所有抽象方法，否则同样不能实例化
- 抽象类适合定义“统一接口”，例如不同图形都提供 `area()` 和 `perimeter()`
