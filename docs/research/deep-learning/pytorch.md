---
icon: fontawesome/solid/cancer
tags:
  - deep-learning

---

> 2023.9.9
>
> 王特起

# Pytorch基础学习

## 实验可复现性配置

### 随机种子

```python
torch.manual_seed(42)
```

### 确定性计算

```python
torch.backends.cudnn.deterministic = True
torch.backends.cudnn.benchmark = False
```

## 张量

### 创建张量

1. 创建张量，默认数据类型是 `torch.int64`

    ```python
    torch.tensor([1, 2, 3, 4])
    ```

2. 创建服从 ==标准正态分布== 的指定形状张量

    ```python
    torch.randn(2, 3)
    ```

### 张量的基本属性

1. 获取维数

    ```python
    tensor.ndim
    ```

2. 获取形状

    ```python
    tensor.shape
    ```

3. 获取数据类型

    ```python
    tensor.dtype
    ```

4. 获取设备类型

    ```python
    tensor.device
    ```

5. 获取张量中元素个数

    ```python
    tensor.numel()
    ```

### 张量的维度操作

1. 重塑张量，改变张量的形状，会与原始张量 ==共享底层数据==

    ```python
    tensor.view(1, 6)
    ```

2. 升维和降维，会与原始张量 ==共享底层数据==

    - 在指定维度位置添加一个大小为1的维度

        ```python
        tensor.unsqueeze()
        ```

    - 移除大小为1的维度

        ```python
        tensor.squeeze()
        ```

### 张量的复制

1. `.data` 属性复制

    会与原始张量 ==共享底层数据==，并从计算图中 ==分离==，但 ==不安全==

2. `.detach()` 方法复制

    会与原始张量 ==共享底层数据==，并从计算图中 ==分离==，但 ==安全==

3. `.clone()` 方法复制

    会创建 ==新的副本==，不会从计算图中 ==分离==

> [!Tip]
>
> *何为安全之说？*
>
> ==原地修改== 参与梯度计算的张量是不被允许的，因为会破坏梯度。
>
> 对于用 `.detach()` 复制会在原地修改时直接 ==报错==，所以是安全的；而用 `.data` 复制会根据原地修改后的值计算 ==错误的梯度==，且==不会报错==，所以不安全

### 张量数据类型的转换

1. 数据类型转换为 `torch.float32`

    ```python
    tensor.float()
    ```

### 张量的数据结构类型转换

1. Numpy数组和PyTorch张量相互转换

    - 将 **Numpy数组** 转换成 **PyTorch张量**，会与原始Numpy数组 ==共享底层数据==

        ```python
        torch.as_tensor(arr)
        ```

    - 将 **PyTorch张量** 转换回 **Numpy数组**，会与原始张量 ==共享底层数据==

        ```python
        tensor.numpy()
        ```

2. PIL图像和PyTorch图像张量相互转换

    PIL图像形状是 `HWC`，PyTorch张量形状是 `NCHW`

    - 将 **PIL图像** 转换 **PyTorch张量**

        ```python
        from torchvision import transforms
        
        ToTensor()(PIL)
        ```

    - 将 **PyTorch张量** 转换回 **PIL图像**
    
        ```python
        ToPILImage()(tensor)
        ```

### 张量的设备分配

1. GPU的基本信息

    - 检查GPU是否可用

        ```python
        torch.cuda.is_available()
        ```

    - 查看GPU数量

        ```python
        torch.cuda.device_count()
        ```

    - 查看GPU型号

        ```python
        torch.cuda.get_device_name(i)
        ```

2. 定义设备

    ```python
    device = torch.device('cuda:0' if torch.cuda.is_available() else 'cpu')
    ```

3. 将张量 ==发送== 到指定的设备

    ```python
    .to(device)
    ```

4. 将 **GPU张量** 转为 **CPU张量**

    ```python
    .cpu()
    ```

### 张量的梯度

1. `requires_grad` 属性控制梯度的开关

    - 直接将 `requires_grad` 属性设置为True，表明有梯度

    - 用 `tensor.requires_grad_()` 方法将属性设置为True

        > [!Tip]
        >
        > ==下划线(_)结尾== 的方法，表示在 ==原地== 修改，会修改 ==底层数据==

2. `.backward()` 方法计算梯度

3. `.grad` 属性查看梯度值

4. `.grad.zero_()` 方法将梯度归零

    因为PyTorch会 ==累积== 梯度，需要在参数更新 ==之后== 将梯度 ==归零==

5. `torch.no_grad()` 方法临时 ==禁用== 梯度计算

    在该作用域内执行的运算不会被 Autograd 记录，因此 ==不会构建新的计算图==

### 张量的数学函数

1. 指定维度上最大值索引

    ```python
    torch.argmax(,dim)
    ```

2. 批量矩阵乘法

    ```python
    torch.bmm()
    torch.matmul()
    ```

3. 判断所有元素是否为True

    ```python
    .all()
    ```

4. 使mask中为True的位置被替换为指定值

    ```python
    .masked_fill(mask)
    ```







































































