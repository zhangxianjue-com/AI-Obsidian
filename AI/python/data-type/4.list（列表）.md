列表（`list`）可以按顺序保存**多个**值。列表的特点：

- **有序**：元素按插入顺序排列，可以用索引访问
- **可变**：可以添加、删除、修改元素
- **可重复**：允许出现相同的元素
- **可混合**：元素可以是不同类型

## 创建列表

```python
a = []                     # 空列表
b = [1, 2, 3]              # 整数列表
c = [1, "two", 3.0, True]  # 混合类型

print(a, b, c)
# [] [1, 2, 3] [1, 'two', 3.0, True]
```

用 `list()` 把其他可迭代对象转成列表，用 `*` 重复列表：

```python
print(list("abc"))     # ['a', 'b', 'c']
print(list(range(5)))  # [0, 1, 2, 3, 4]
print([0] * 5)         # [0, 0, 0, 0, 0]
```

## 索引与切片

```python
a = [10, 20, 30, 40, 50]

print(a[0])   # 10
print(a[-1])  # 50，负数索引从末尾开始
print(a[-2])  # 40
```

切片返回一个**新列表**：

```python
print(a[1:4])   # [20, 30, 40]
print(a[:3])    # [10, 20, 30]
print(a[::2])   # [10, 30, 50]
print(a[::-1])  # [50, 40, 30, 20, 10]，反转
```

## 添加元素

- `append` 把参数当作**一个整体**添加；`a.append([4, 5])` 会得到嵌套列表
- `extend` 会把可迭代对象的元素逐个加入

```python
a = [1, 2]

a.append(3)       # 末尾追加一个元素
print(a)          # [1, 2, 3]

a.extend([4, 5])  # 追加另一个可迭代对象的所有元素
print(a)          # [1, 2, 3, 4, 5]

a.insert(0, 0)    # 在索引 0 之前插入
print(a)          # [0, 1, 2, 3, 4, 5]
```

## 删除元素

- `pop` 索引越界时抛 `IndexError`
- `remove(x)` 找不到 x 时抛 `ValueError`
- 也可以用 `del a[0]`、`del a[1:3]` 按位置删除

```python
a = [1, 2, 3, 4]

print(a.pop())  # 4，删除并返回最后一个元素
print(a)        # [1, 2, 3]

print(a.pop(0)) # 1，删除并返回指定索引的元素
print(a)        # [2, 3]

a.remove(2)     # 按值删除第一个匹配项，返回 None
print(a)        # [3]

a.clear()       # 清空列表
print(a)        # []
```

## 查找与统计

```python
a = [1, 2, 2, 3]

print(a.index(2))  # 1，第一个 2 的索引
print(a.count(2))  # 2
print(2 in a)      # True
print(5 in a)      # False
print(len(a))      # 4
```

## 排序与反转

- `sort()` 原地排序，**返回 `None`**

```python
a = [3, 1, 2]

a.sort()
print(a)  # [1, 2, 3]

a.sort(reverse=True)
print(a)  # [3, 2, 1]

words = ["bb", "a", "ccc"]
words.sort(key=len)
print(words)  # ['a', 'bb', 'ccc']
```

- `sorted(a)` 返回排好序的新列表，原列表不变

```python
a = [3, 1, 2]
print(sorted(a))  # [1, 2, 3]
print(a)          # [3, 1, 2]
```

- `a.reverse()` 反转：

```python
a = [1, 2, 3]
a.reverse()       # 原地反转，返回 None
print(a)          # [3, 2, 1]

print(a[::-1])    # [1, 2, 3]，切片返回新列表
```
