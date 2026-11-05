---
jupyter:
  jupytext:
    cell_metadata_filter: -all
    formats: ipynb,md
    text_representation:
      extension: .md
      format_name: markdown
      format_version: "1.3"
      jupytext_version: 1.17.1
  kernelspec:
    display_name: Python (.jupymd)
    language: python
    name: jupymd-.jupymd-a04f123165
---

标量（scalar）指单个值，是最基本的数据单位。Python 的标量类型主要有：

| 类型   | 关键字     | 示例                  |
| ------ | ---------- | --------------------- |
| 整数   | `int`      | `42`、`-7`、`10**100` |
| 浮点数 | `float`    | `3.14`、`1e-3`        |
| 布尔值 | `bool`     | `True`、`False`       |
| 字符串 | `str`      | `"hello"`、`'hi'`     |
| 空值   | `NoneType` | `None`                |

用 `type()` 查看一个值的类型：

```python
print(type(42))        # <class 'int'>
print(type(3.14))      # <class 'float'>
print(type(True))      # <class 'bool'>
print(type("hello"))   # <class 'str'>
print(type(None))      # <class 'NoneType'>
```

## 变量

变量是对象的名字（引用），赋值时创建，不需要声明类型：

```python
x = 10
name = "Alice"
pi = 3.14
is_ready = True

print(x)
print(name)
print(pi)
print(is_ready)
```

## 算术运算符

| 运算符 | 名称             | 示例     | 结果  |
| ------ | ---------------- | -------- | ----- |
| `+`    | 加               | `7 + 2`  | `9`   |
| `-`    | 减               | `7 - 2`  | `5`   |
| `*`    | 乘               | `7 * 2`  | `14`  |
| `/`    | 除法（真除法）   | `7 / 2`  | `3.5` |
| `//`   | 整除（向下取整） | `7 // 2` | `3`   |
| `%`    | 取余             | `7 % 2`  | `1`   |
| `**`   | 幂               | `7 ** 2` | `49`  |

```python
print(7 + 2)   # 9
print(7 - 2)   # 5
print(7 * 2)   # 14
print(7 / 2)   # 3.5
print(7 // 2)  # 3
print(7 % 2)   # 1
print(7 ** 2)  # 49
```

## 逻辑运算符

| 运算符 | 含义   | 示例             | 结果    |
| ------ | ------ | ---------------- | ------- |
| `and`  | 逻辑与 | `True and False` | `False` |
| `or`   | 逻辑或 | `True or False`  | `True`  |
| `not`  | 逻辑非 | `not True`       | `False` |

```python
print(True and False)  # False
print(True or False)   # True
print(not True)        # False

print(bool(0))         # False
print(bool(""))        # False
print(bool("hi"))      # True
```

## 比较运算符

| 运算符     | 含义               |
| ---------- | ------------------ |
| `==`       | 等于               |
| `!=`       | 不等于             |
| `>`、`<`   | 大于、小于         |
| `>=`、`<=` | 大于等于、小于等于 |

```python
x = 5
print(x == 5)      # True
print(x != 5)      # False
print(1 < x < 10)  # True，Python 支持链式比较
```
