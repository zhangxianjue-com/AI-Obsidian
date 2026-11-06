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

NumPy 是 Python 最常用的科学计算库，核心是 `ndarray`（N 维数组），支持高效的向量化运算。它**不是 Python 标准库**，需要单独安装：

```bash
pip install numpy
```

```python
import numpy as np

print(np.__version__)  # 已安装的版本号
```

约定俗成用 `np` 作为别名。

## 创建数组

| 函数                             | 说明                                |
| -------------------------------- | ----------------------------------- |
| `np.array([v1, v2])`             | 创建指定数组                        |
| `np.zeros(shape)`                | 全 0 数组                           |
| `np.ones(shape)`                 | 全 1 数组                           |
| `np.full(shape, value)`          | 全部填充指定值                      |
| `np.arange(start, stop[, step])` | 类似 `range`，不包含 stop           |
| `np.linspace(start, stop, num)`  | 在区间内均匀取 `num` 个点，包含两端 |
| `np.eye(n)`                      | n × n 单位矩阵                      |

```python
import numpy as np

a = np.array([1, 2, 3])
print(a)  # [1 2 3]

b = np.array([[1, 2], [3, 4]])
print(b)
# [[1 2]
#  [3 4]]

print(np.zeros((2, 3)))
# [[0. 0. 0.]
#  [0. 0. 0.]]

print(np.ones((2, 2)))
# [[1. 1.]
#  [1. 1.]]

print(np.full((2, 2), 7))
# [[7 7]
#  [7 7]]

print(np.arange(0, 10, 2))  # [0 2 4 6 8]
print(np.linspace(0, 1, 5)) # [0.   0.25 0.5  0.75 1.  ]

print(np.eye(3))
# [[1. 0. 0.]
#  [0. 1. 0.]
#  [0. 0. 1.]]
```

## 数组属性

```python
a = np.array([[1, 2, 3], [4, 5, 6]])

print(a.shape)  # (2, 3)，形状：2 行 3 列
print(a.ndim)   # 2，维度数
print(a.size)   # 6，元素总数
print(a.dtype)  # 元素类型，可能是 int32 或 int64（取决于平台和版本）

print(a.T)
# [[1 4]
#  [2 5]
#  [3 6]]
```

## 数据类型与转换

```python
a = np.array([1, 2, 3], dtype=np.float64)
print(a)        # [1. 2. 3.]
print(a.dtype)  # float64

b = a.astype(np.int32)
print(b)        # [1 2 3]
print(b.dtype)  # int32
```

## 索引与切片

一维数组：

```python
a = np.array([10, 20, 30, 40, 50])
print(a[0], a[-1])  # 10 50
print(a[1:4])       # [20 30 40]
```

二维数组用逗号分隔维度的索引：

```python
b = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])

print(b[0, 0])  # 1
print(b[1])     # [4 5 6]，第二行
print(b[:, 1])  # [2 5 8]，第二列

print(b[0:2, 1:3])
# [[2 3]
#  [5 6]]
```

布尔索引和花式索引：

```python
c = np.array([1, 5, 8, 12, 3])

print(c[c > 5])      # [ 8 12]，选出满足条件的元素
print(c[[0, 2, 4]])  # [1 8 3]，按索引列表取元素
```
