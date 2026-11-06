函数用 `def` 定义，把一段逻辑封装起来，便于复用和测试。

## 定义与调用

```python
def greet(name):
    """返回一句问候语。"""
    return f"Hello, {name}!"

print(greet("Alice"))  # Hello, Alice!
```

- `def 函数名(参数):` 定义函数，函数体缩进
- `return` 返回结果；没有 `return` 时函数返回 `None`

## 参数

### 位置参数与关键字参数

```python
def introduce(name, age):
    return f"{name} is {age} years old."

print(introduce("Alice", 25))           # 位置参数
print(introduce(age=25, name="Alice"))  # 关键字参数
```

### 默认参数

```python
def greet(name, greeting="Hello"):
    return f"{greeting}, {name}!"

print(greet("Alice"))                # Hello, Alice!
print(greet("Bob", "Hi"))            # Hi, Bob!
print(greet("Bob", greeting="Hey"))  # Hey, Bob!
```

默认值在函数**定义时**计算一次，所以不要用列表、字典等可变对象作默认值（见“常见坑”）。

### 可变参数 \*args 和 \*\*kwargs

```python
def add_all(*numbers):
    return sum(numbers)

print(add_all(1, 2, 3))        # 6
print(add_all(1, 2, 3, 4, 5))  # 15
```

`*numbers` 把任意数量的位置参数收集成**元组**。

```python
def show_info(**info):
    for key, value in info.items():
        print(f"{key}: {value}")

show_info(name="Alice", age=25)
# name: Alice
# age: 25
```

`**info` 把任意数量的关键字参数收集成**字典**。

组合使用时：

```python
def example(a, b=2, *args, c=3, **kwargs):
    print(a, b, args, c, kwargs)

example(1)                    # 1 2 () 3 {}
example(1, 4, 5, 6, c=7, d=8) # 1 4 (5, 6) 7 {'d': 8}
```

参数顺序：位置参数 → 默认参数 → `*args` → 仅关键字参数 → `**kwargs`。

### 解包调用

```python
def add(a, b):
    return a + b

print(add(*[3, 4]))             # 7，列表解包成位置参数
print(add(**{"a": 3, "b": 4}))  # 7，字典解包成关键字参数
```

## 返回值

`return` 可以返回多个值，实际返回的是元组：

```python
def min_max(numbers):
    return min(numbers), max(numbers)

low, high = min_max([3, 1, 4, 1, 5])
print(low, high)  # 1 5
```

函数遇到 `return` 就结束，后面的代码不会执行。

## 作用域

函数内部赋值的变量是局部变量，不会影响外部同名变量：

```python
x = 10

def show():
    x = 20
    print(x)

show()      # 20
print(x)    # 10
```

要在函数内修改全局变量时用 `global`（通常不推荐）：

```python
count = 0

def increment():
    global count
    count += 1

increment()
print(count)  # 1
```

嵌套函数中修改外层函数的变量用 `nonlocal`：

```python
def outer():
    n = 0

    def inner():
        nonlocal n
        n += 1
        return n

    return inner

counter = outer()
print(counter())  # 1
print(counter())  # 2
```

## lambda 匿名函数

```python
square = lambda x: x ** 2
print(square(5))  # 25

pairs = [(1, "b"), (3, "a"), (2, "c")]
pairs.sort(key=lambda item: item[0])
print(pairs)  # [(1, 'b'), (2, 'c'), (3, 'a')]
```

lambda 适合写简短的匿名函数，复杂逻辑还是用 `def`。

## 递归

函数可以调用自身，但必须有终止条件：

```python
def factorial(n):
    if n <= 1:          # 终止条件
        return 1
    return n * factorial(n - 1)

print(factorial(5))  # 120
```

递归层数过深会触发 `RecursionError`。

## 类型注解

```python
def add(a: int, b: int = 0) -> int:
    return a + b

print(add(3, 4))  # 7
```

类型注解只是提示，Python 不会强制检查。
