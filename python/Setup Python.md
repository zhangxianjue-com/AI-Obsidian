> python 编程

## 安装 Python

去 [Python 官网](https://www.python.org/downloads) 下载安装包

安装后，打开终端或命令提示符，输入 `python --version` 如果能显示版本号就说明成功了。

## 使用 JupyMD 插件

> `.jupymd` 是本地虚拟环境，不会被提交到 Git，换电脑后需要重新创建（直接复制旧电脑的 `.jupymd` 会因路径和二进制不兼容而报错）。

> 如果提示缺少 Jupytext 或 Jupyter tooling，按 JupyMD 的提示为 tooling 环境安装即可。

JupyMD 的设计目标就是把 Jupyter 的交互式编程体验整合进 Obsidian。

JupyMD 安装步骤如下：

1. 安装 Python（3.10 或更高版本），安装时勾选 **Add python.exe to PATH**
2. 克隆仓库，并用 Obsidian 打开
3. 启用 JupyMD 插件
   - 仓库中已包含 `.obsidian/plugins/` 时插件会一起同步；否则在 Obsidian 社区插件市场搜索 JupyMD 安装
4. 打开含 Python 代码块的笔记，点击运行按钮
5. 在 “Select a kernel source...” 中选择 **Python environments...**
6. 选择 **Create a virtual environment in the vault**，等待插件创建 `.jupymd` 并安装 IPyKernel
7. 选择生成的 `.jupymd` 解释器，即可运行代码

在你的 Markdown 笔记中，像平常一样写一个 Python 代码块（使用 ```python），代码块上方或附近通常会出现一个“运行”按钮。点击它，代码就会执行，输出结果会直接显示在代码块下方。

```python
print("hi")
```

## Link

[[data-type]] <!-- 数据类型 -->
[[opp]] <!-- 面向对象编程 -->
[[stdlib]] <!-- 标准库 -->
[[package]] <!-- 第三方库 -->
