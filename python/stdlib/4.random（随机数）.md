`random` 是 Python 标准库中的伪随机数模块，用于生成随机数、随机选择和打乱顺序。使用前导入：

```python
import random
```

## 随机种子 random.seed

`random.seed(a)` 设置随机种子。**种子相同，生成的随机数序列也相同**，便于复现结果：

```python
import random

random.seed(42)
print(random.random())  # 0.6394267984578837

random.seed(42)
print(random.random())  # 0.6394267984578837
```

## 随机浮点数

| 函数                   | 说明                           |
| ---------------------- | ------------------------------ |
| `random.random()`      | 返回 `[0.0, 1.0)` 之间的浮点数 |
| `random.uniform(a, b)` | 返回 `a` 到 `b` 之间的浮点数   |

```python
random.seed(42)
print(random.random())        # 0.6394267984578837
print(random.uniform(1, 10))  # 6.754841186120954
```

## 随机整数

| 函数                                    | 说明                                                    |
| --------------------------------------- | ------------------------------------------------------- |
| `random.randint(a, b)`                  | 返回 `[a, b]` 之间的整数，**包含两端**                  |
| `random.randrange(start, stop[, step])` | 从 `range(start, stop, step)` 中取一个，**不包含 stop** |

```python
random.seed(42)
print(random.randint(1, 6))        # 6
print(random.randrange(0, 10, 2))  # 0（只会取 0、2、4、6、8）
```

## 从序列中随机选择

| 函数                                            | 说明                                        |
| ----------------------------------------------- | ------------------------------------------- |
| `random.choice(seq)`                            | 随机返回一个元素；序列为空时抛 `IndexError` |
| `random.choices(population, weights=None, k=1)` | 可重复地取 `k` 个，返回列表，支持权重       |
| `random.sample(population, k)`                  | **不重复**地取 `k` 个，返回列表             |

```python
random.seed(42)
print(random.choice(["石头", "剪刀", "布"]))  # 布
print(random.choices("ABC", k=3))             # ['B', 'A', 'A']（可能重复）

# 这里 A 被选中的概率是 B 的 9 倍。
print(random.choices(["A", "B"], weights=[9, 1], k=5))  # ['A', 'A', 'A', 'A', 'A']

# `sample` 的 `k` 大于序列长度时会抛 `ValueError`。
print(random.sample([1, 2, 3, 4, 5], 2))      # [1, 5]（不会重复）
```

## 打乱顺序 random.shuffle

`random.shuffle(x)` **原地**打乱列表，返回 `None`：

```python
random.seed(42)
cards = [1, 2, 3, 4, 5]
random.shuffle(cards)
print(cards)  # [4, 2, 3, 5, 1]
```
