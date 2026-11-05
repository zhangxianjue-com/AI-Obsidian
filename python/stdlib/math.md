---
jupyter:
  jupytext:
    cell_metadata_filter: -all
    formats: ipynb,md
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.3'
      jupytext_version: 1.17.1
  kernelspec:
    display_name: Python (.jupymd)
    language: python
    name: jupymd-.jupymd-a04f123165
---

`math` 是 Python 标准库中的数学模块，提供常用数学常量、幂与对数、三角函数等函数。使用前先导入：

```python
import math
```

## 常用常量

| 常量       | 近似值              | 说明           |
| ---------- | ------------------- | -------------- |
| `math.pi`  | `3.141592653589793` | 圆周率 π       |
| `math.e`   | `2.718281828459045` | 自然对数的底 e |
| `math.tau` | `6.283185307179586` | 2π             |

```python
import math

print(math.pi)   # 3.141592653589793
print(math.e)    # 2.718281828459045
print(math.tau)  # 6.283185307179586
```

## 平方根 math.sqrt

`math.sqrt(x)` 返回 x 的平方根，结果总是浮点数。

```python
print(math.sqrt(16))  # 4.0
print(math.sqrt(2))   # 1.4142135623730951
print(math.sqrt(0))   # 0.0
```

## 三角函数 sin、cos

math.sin / math.cos / math.tan 返回的都是一个 float，表示这个角对应的三角比值（不是角度）。输入是弧度`math.radians(deg) 角度转弧度`，输出是无单位的实数。

从单位圆理解最直观：角 θ 的终边与单位圆交于 (x, y)，则

sin(θ) → y（纵坐标），范围 [-1, 1]
cos(θ) → x（横坐标），范围 [-1, 1]
tan(θ) = sin(θ) / cos(θ) → y / x，可以取任意实数

```python
print(math.sin(math.pi / 2))  # 1.0  —— 90° 时终边在正上方，y = 1
print(math.cos(0))            # 1.0  —— 0° 时终边在正右方，x = 1

# 角度转弧度
print(math.sin(math.radians(30)))  # 0.49999999999999994
```

## 指数函数 math.exp

`math.exp(x)` 返回 e 的 x 次方，等价于 `math.e ** x`，结果总是浮点数。

```python
print(math.exp(0))  # 1.0
print(math.exp(1))  # 2.718281828459045
print(math.exp(2))  # 7.38905609893065
```

## 对数函数 math.log

`math.log(x)` 是自然对数（以 e 为底）；`math.log(x, base)` 可以指定底数。

```python
print(math.log(1))        # 0.0
print(math.log(math.e))   # 1.0
print(math.log(8, 2))     # 3.0
print(math.log(100, 10))  # 2.0
```

常用变体：

| 函数            | 等价写法              | 说明          |
| --------------- | --------------------- | ------------- |
| `math.log(x)`   | `math.log(x, math.e)` | 自然对数 ln x |
| `math.log2(x)`  | `math.log(x, 2)`      | 以 2 为底     |
| `math.log10(x)` | `math.log(x, 10)`     | 以 10 为底    |

```python
print(math.log2(8))     # 3.0
print(math.log10(1000)) # 3.0
```

## 其他常用函数

| 函数                             | 说明                                              |
| -------------------------------- | ------------------------------------------------- |
| `math.floor(x)` / `math.ceil(x)` | 向下 / 向上取整，返回 `int`                       |
| `math.fabs(x)`                   | 绝对值，返回 `float`                              |
| `math.pow(x, y)`                 | 幂，返回 `float`（`x ** y` 对整数可能返回 `int`） |
| `math.isclose(a, b)`             | 判断两个浮点数是否近似相等                        |
| `math.inf` / `math.nan`          | 无穷大 / 非数字                                   |

```python
print(math.floor(3.7))  # 3
print(math.ceil(3.2))   # 4
print(math.fabs(-5))    # 5.0
print(math.pow(2, 10))  # 1024.0
print(math.inf)         # inf
print(math.nan)         # nan
```
