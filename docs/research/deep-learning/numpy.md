---
icon: fontawesome/solid/leo
tags:
  - deep-learning

---

> 2023.9.8
>
> 王特起

# Numpy基础学习

## 实验可复现性配置

### 随机种子

```python
np.random.seed(42)
```

## 数组

### 创建数组

1. 生成随机数组

    - 创建给定形状 $N*1$ 的数组，服从 $[0,1)$ 区间均匀分布

        ```python
        np.random.rand(N,1)
        ```

    - 创建给定形状 $N*1$ 的数组，服从标准正态分布

        ```python
        np.random.randn(N,1)
        ```

2. 创建等间距的一维数组

    - 步长为1

        ```python
        np.arange(N)
        ```

### 数组的基本属性

1. 获取形状

    ```python
    arr.shape
    ```

### 数组的维度操作

1. 维度拼接

    - 沿 ==增加的新维度== axis拼接

        ```python
        np.stack((arr1, arr2), axis=0)
        ```

    - 沿 ==指定维度== 拼接

        ```python
        np.concatenate((arr1, arr2), axis=0)
        ```

2. 维度交换

    - 一次交换两个维度

        ```python
        np.transpose(arr, [1, 0, 2])
        ```

### 数组的数学函数

1. 原地打乱一维数组

    ```python
    np.random.shuffle(arr)
    ```

2. 数组沿指定维度求均值

    ```python
    np.mean(arr, axis=0)
    ```

3. 花式索引

    允许利用整数数组进行索引



























































