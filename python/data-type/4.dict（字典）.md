字典（`dict`）用于保存**键值对**（key-value）映射，适合按名字快速查找数据。特点：

- 每个元素是 `键: 值` 对
- 键必须唯一；重复赋值时后一个覆盖前一个
- 键必须**可哈希**（如字符串、数字、元组），列表和字典不能作键
- 值可以是任意类型
- 可变：可以增删改

## 创建字典

```python
person = {"name": "Alice", "age": 25, "city": "Beijing"}
print(person)
# {'name': 'Alice', 'age': 25, 'city': 'Beijing'}

print(dict(name="Alice", age=25))
# {'name': 'Alice', 'age': 25}

print(dict([("a", 1), ("b", 2)]))
# {'a': 1, 'b': 2}

print(dict.fromkeys(["a", "b"], 0))
# {'a': 0, 'b': 0}
```

## 访问元素

```python
person = {"name": "Alice", "age": 25}

print(person["name"])            # Alice
print(person.get("age"))         # 25
print(person.get("height"))      # None
print(person.get("height", 170)) # 170，键不存在时返回默认值

```

## 添加与修改

```python
person = {"name": "Alice", "age": 25}

person["age"] = 26                      # 键存在：修改
person["email"] = "alice@example.com"   # 键不存在：新增
print(person)
# {'name': 'Alice', 'age': 26, 'email': 'alice@example.com'}

person.update({"city": "Beijing", "age": 30})
print(person)
# {'name': 'Alice', 'age': 30, 'email': 'alice@example.com', 'city': 'Beijing'}
```

## 删除元素

```python
person = {"name": "Alice", "age": 25, "city": "Beijing"}

print(person.pop("age"))      # 25，删除并返回对应的值
print(person)                 # {'name': 'Alice', 'city': 'Beijing'}

print(person.pop("height", None))  # None，键不存在时返回默认值
# person.pop("height")             # 不传默认值会抛 KeyError

del person["name"]
print(person)                 # {'city': 'Beijing'}

person.clear()
print(person)                 # {}
```

## 遍历字典

直接遍历字典得到的是**键**：

```python
scores = {"math": 90, "english": 85, "python": 95}

for subject in scores:
    print(subject)
# math
# english
# python
```

## 合并字典

```python
d1 = {"a": 1, "b": 2}
d2 = {"b": 3, "c": 4}

print(d1 | d2)  # {'a': 1, 'b': 3, 'c': 4}，重复的键以后一个为准
print(d1)       # {'a': 1, 'b': 2}，| 返回新字典

d1 |= d2        # 原地合并
print(d1)       # {'a': 1, 'b': 3, 'c': 4}
```

`|` 运算符需要 Python 3.9+；旧写法是 `{**d1, **d2}`。
