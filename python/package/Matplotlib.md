Matplotlib 是 Python 最常用的绘图库，可以绘制折线图、散点图、柱状图、直方图等。它**不是标准库**，需要单独安装：

```bash
pip install matplotlib
```

```python
import matplotlib.pyplot as plt

%matplotlib inline  # Jupyter/JupyMD 的魔法命令，让图形内嵌显示
```

约定俗成用 `plt` 作为别名。

## 基本用法

最简单的折线图：

- `plt.plot(x, y)` 创建折线图
- `plt.show()` 显示图形
- 不调用 `show()` 时，在普通脚本中可能看不到图

```python
import matplotlib.pyplot as plt

x = [1, 2, 3, 4]
y = [1, 4, 9, 16]

plt.plot(x, y)
plt.show()
```

更推荐使用 **Figure / Axes 面向对象写法**：

- **Figure**：整张画布
- **Axes**：画布上的一个坐标系（子图）
- `figsize=(宽, 高)` 的单位是英寸
- 多子图或复杂布局时，面向对象写法更清晰

```python
import matplotlib.pyplot as plt

fig, ax = plt.subplots(figsize=(6, 4))  # 创建画布和坐标轴
ax.plot([1, 2, 3, 4], [1, 4, 9, 16])
ax.set_title("Square Numbers")
ax.set_xlabel("x")
ax.set_ylabel("y")
plt.show()
```

## 折线图

`plt.plot` 用来画折线图，可以连续调用多次绘制多条曲线：

线型：

| 写法             | 效果         |
| ---------------- | ------------ |
| `"-"`            | 实线（默认） |
| `"--"`           | 虚线         |
| `"-."`           | 点划线       |
| `":"`            | 点线         |
| `"None"` 或 `""` | 不画线       |

常用标记：`"o"` 圆、`"s"` 方块、`"^"` 三角形、`"*"` 星形、`"+"` 加号、`"x"` 叉号。

```python
x = np.linspace(0, 2 * np.pi, 10)

plt.plot(
    x, np.sin(x),
    color="red",      # 颜色
    linewidth=2,      # 线宽
    linestyle="--",   # 线型
    marker="o",       # 数据点标记
    markersize=5,     # 标记大小
    label="sin(x)",
)

plt.legend()
plt.show()
```

## 散点图

`plt.scatter` 用两个数组分别表示点的横纵坐标：

```python
import numpy as np
import matplotlib.pyplot as plt

rng = np.random.default_rng(42)
x = rng.normal(0, 1, 100)
y = 2 * x + rng.normal(0, 1, 100)

plt.scatter(x, y, s=30, c="tab:blue", alpha=0.7)

plt.title("Scatter Plot")
plt.xlabel("x")
plt.ylabel("y")
plt.grid(True, alpha=0.3)
plt.show()
```

- `s`：点的大小
- `c`：颜色
- `alpha`：透明度，`0` 完全透明、`1` 完全不透明
- `marker`：点的形状，规则和折线图相同

## 自定义功能

### 颜色

```python
plt.plot(x, np.sin(x), color="red")             # 颜色名称
plt.plot(x, np.cos(x), color="#FF5733")         # 十六进制
plt.plot(x, x / 10, color=(0.2, 0.6, 0.8))      # RGB（0 到 1）
plt.show()
```

常用单字母：`r` 红、`g` 绿、`b` 蓝、`c` 青、`m` 品红、`y` 黄、`k` 黑、`w` 白。

### 标题、坐标轴与范围

```python
fig, ax = plt.subplots(figsize=(6, 4))
ax.plot(x, np.sin(x))

ax.set_title("Title", fontsize=14)
ax.set_xlabel("x", fontsize=12)
ax.set_ylabel("y", fontsize=12)
ax.set_xlim(0, 2 * np.pi)   # x 轴范围
ax.set_ylim(-1.5, 1.5)      # y 轴范围
ax.set_xticks([0, np.pi, 2 * np.pi])
ax.set_yticks([-1, 0, 1])

plt.show()
```

使用 `plt` 函数时对应写法是 `plt.title`、`plt.xlabel`、`plt.xlim`、`plt.xticks` 等。

### 图例与网格

```python
plt.plot(x, np.sin(x), label="sin")
plt.plot(x, np.cos(x), label="cos")

plt.legend(loc="upper right")                # 显示图例
plt.grid(True, linestyle="--", alpha=0.5)    # 显示网格
plt.show()
```

`legend` 的常用位置：`"best"`、`"upper right"`、`"upper left"`、`"lower right"`、`"lower left"`、`"center"`。

### 文字与注释

```python
fig, ax = plt.subplots(figsize=(6, 4))
ax.plot(x, np.sin(x))
ax.set_title("Annotation")

ax.annotate(
    "peak",                       # 注释文字
    xy=(np.pi / 2, 1),            # 箭头指向的位置
    xytext=(2, 1.2),              # 文字位置
    arrowprops={"arrowstyle": "->"},
)

plt.show()
```

### 子图

```python
fig, axes = plt.subplots(1, 2, figsize=(10, 4))

axes[0].plot(x, np.sin(x))
axes[0].set_title("sin")

axes[1].plot(x, np.cos(x))
axes[1].set_title("cos")

plt.tight_layout()  # 自动调整子图间距
plt.show()
```

`plt.subplots(行数, 列数)` 返回 Figure 和 Axes 数组；只有一个子图时，`axes` 是单个对象而不是数组。

### 样式

```python
plt.style.use("ggplot")   # 使用内置样式

fig, ax = plt.subplots()
ax.plot(x, np.sin(x))
ax.set_title("ggplot style")
plt.show()

plt.style.use("default")  # 恢复默认样式
```

用 `plt.style.available` 查看所有内置样式，常用的有 `"ggplot"`、`"dark_background"`、`"seaborn-v0_8"`。

## 中文显示

Matplotlib 默认字体不支持中文，需要手动设置：

```python
plt.rcParams["font.sans-serif"] = ["Microsoft YaHei", "SimHei"]
plt.rcParams["axes.unicode_minus"] = False  # 让负号正常显示
```

- Windows 常用 `"Microsoft YaHei"`（微软雅黑）或 `"SimHei"`（黑体）
- macOS 可以用 `"PingFang SC"`
- 设置后中文字体不生效时，检查系统是否安装了对应字体
