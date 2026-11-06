Python 用**缩进**（通常 4 个空格）划分代码块。条件判断和循环都以冒号 `:` 结尾，下面缩进的代码属于这个代码块。

## 条件判断 if

按顺序判断，满足哪个分支就执行哪个：

```python
score = 85

if score >= 90:
    grade = "A"
elif score >= 80:
    grade = "B"
elif score >= 60:
    grade = "C"
else:
    grade = "D"

print(grade)  # B
```

- `if` 可以单独使用，`elif` 和 `else` 都是可选的
- 条件不需要加括号，但冒号不能少
- `elif` 可以有多个，`else` 最多一个，放在最后

## match 语句

Python 3.10+ 支持 `match`，适合按多个固定值分支：

```python
command = "start"

match command:
    case "start":
        print("启动")  # 启动
    case "stop":
        print("停止")
    case _:
        print("未知命令")
```

`case _` 是默认分支，相当于 `else`。

## for 循环

`for` 用来遍历一个可迭代对象（列表、字符串、`range`、字典等）：

```python
for i in range(5):
    print(i)
# 0
# 1
# 2
# 3
# 4


# 遍历序列
fruits = ["apple", "banana", "cherry"]

for fruit in fruits:
    print(fruit)
# apple
# banana
# cherry

for ch in "abc":
    print(ch)
# a
# b
# c


# 遍历字典
scores = {"math": 90, "english": 85}

for subject, score in scores.items():
    print(subject, score)
# math 90
# english 85
```

## while 循环

条件为真时反复执行，适合不知道循环次数的场景：

```python
count = 1
while count <= 5:
    print(count)
    count += 1
# 1
# 2
# 3
# 4
# 5
```

- 循环体里必须有能让条件最终变为假的语句，否则会**死循环**
- 常用 `while True:` 配合 `break` 使用

## break 与 continue

```python
for i in range(10):
    if i == 3:
        break       # 立即结束整个循环
    print(i)
# 0
# 1
# 2
```

```python
for i in range(5):
    if i % 2 == 0:
        continue    # 跳过本次，继续下一次
    print(i)
# 1
# 3
```

- `break`：跳出当前这一层循环
- `continue`：跳过本次循环剩余代码，直接进入下一次
- 嵌套循环中，`break` 只跳出**最近的一层**

## 循环的 else

`for` / `while` 可以带 `else`，它在循环**正常结束**（没有被 `break` 打断）时执行：

```python
numbers = [1, 3, 5, 7]

for n in numbers:
    if n % 2 == 0:
        print("找到偶数:", n)
        break
else:
    print("没有偶数")  # 没有偶数
```

这个写法常用于“查找没找到”的场景。

## 嵌套循环与 pass

```python
for i in range(1, 4):
    for j in range(1, 4):
        print(i * j, end=" ")
    print()
# 1 2 3
# 2 4 6
# 3 6 9
```

`print(..., end=" ")` 让输出不换行，内层循环结束后再单独 `print()` 换行。

`pass` 是空语句，用来占位：

```python
for i in range(3):
    pass  # 什么都不做
```
