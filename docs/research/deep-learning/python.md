---
icon: fontawesome/brands/python
tags:
  - deep-learning

---

> 2023.9.7
>
> 王特起

# Python基础学习

## 实验可复现性配置

### 随机种子

```python
random.seed(42)
```

## 数据类型

### 数据类型转换

1. 将数字或字符串转为整型

    ```python
    int()
    ```

### 字符串

1. 连接字符串

    ```python
    .join()
    ```

## 数据结构类型

### 查看数据结构类型

```python
type()
```

### 列表

1. 在列表末尾添加元素

    ```python
    .append()
    ```

### 字典

1. 把另一个字典的键值对更新到字典里

    ```python
    .update()
    ```

2. 得到字典的键值对

    ```python
    .items()
    ```

3. 清空字典

    ```python
    .clear()
    ```

## 迭代器

### 创建迭代器

1. 从 ==可迭代对象== 获取迭代器

    ```python
    iter()
    ```

2. 使用 ==生成器表达式== 创建生成器获取，因为生成器 ==返回== 一个迭代器

    ```python
    (表达式 for 项 in 可迭代对象 if 条件)
    ```

### 检索迭代器

获取迭代器的下一项

```python
next()
```

## 函数

### 内置函数

1. 创建一个可迭代对象，用于for循环

    ```python
    range()
    ```

2. 获取对象的长度

    ```python
    len()
    ```

3. 设置属性值

    ```python
    setattr()
    ```

4. 判断一个对象是否属于某种类型

    ```python
    isinstance()
    ```

### 高阶函数

高阶函数是一个函数 ==构建器==，==返回骨架函数==

### Lambda匿名函数

1. 基本用法

    ```python
    lambda arguments: expression
    ```

2. 与 `map()` 函数结合使用

    `map()` 函数将给定函数应用于可迭代对象的每个元素

3. 与 `fliter()` 函数结合使用

    函数返回 `True` 的元素被保留

## 模块

### os模块

1. 引入

    ```python
    import os
    ```

2. 创建多级目录

    ```python
    os.makedirs(dir,exist_ok=True)
    ```

3. 把目录和文件名合成一个路径

    ```python
    os.path.join(dir,filename)
    ```

4. 获取文件的目录

    ```python
    os.path.dirname()
    ```

### datatime模块

1. 引入

    ```python
    from datatime import datatime
    ```

2. 获取当前时间

    ```python
    datatime.now()
    ```

3. 转换成 ==字符串== 格式

    ```python
    .strftime('%Y-%m-%d_%H:%M:%S')
    ```

### yaml模块

1. 引入

    ```python
    import yaml
    ```

2. 读取 `yaml` 文件

    ```python
    yaml.safe_load()
    ```

3. 将 `python` 字典或列表写入 `yaml` 文件

    ```python
    yaml.safe_dump()
    ```

### argparse模块

1. 引入

    ```python
    import argparse
    ```

2. 创建命令行参数解析对象

    ```python
    argparse.ArgumentParser()
    ```

3. 创建命令行参数

    ```python
    argparse.add_argument()
    ```

4. 解析命令行参数

    ```python
    .parse_known_args()
    ```

### tqdm模块

1. 引入

    ```python
    from tqdm import tqdm
    ```

2. 创建进度条

    ```python
    with tqdm() as pbar:
    ```

3. 设置进度条描述

    ```python
    pbar.set_description()
    ```

4. 设置进度条信息

    ```python
    pbar.set_postfix()
    ```

### Matplotlib模块

1. 引入

    ```python
    import matplotlib.pyplot as plt
    ```

2. 创建图像

    ```python
    plt.figure()
    ```

3. 绘制图像

    ```python
    plt.plot()
    ```

4. 横纵坐标标签

    ```python
    plt.xlabel(), plt.ylabel()
    ```

5. 显示注释

    ```python
    plt.legend()
    ```

## 类

### 构造方法

定义组成类的部分，这些部分是该类的属性

### 方法、_方法和__方法

1. _方法是 ==protectd方法==，只在 ==内部或子类== 调用
2. __方法是 ==private方法==，只在 ==内部== 调用

### 静态方法

可以从 ==类本身== 调用







































































