> 王特起
>
> 2017.2.1

# 编程基础笔记

## Python基础

- 设置种子：`random.seed(42)`

### 数据类型

0. 数据类型转换
    - `int()`将数字或字符串转为整型
0. 字符串
    - `.join()`连接字符串

### 数据结构类型

0. 查看数据结构类型

     使用`type()`查看类型

0. 列表

    - `.append()`方法在末尾添加元素

0. 字典

    - `.update()`把另一个字典的键值对更新到字典里
    - `.items()`得到字典的键值对
    - `.clear()`清空字典

### 迭代器

0. 创建迭代器

    - 使用`iter()`函数从==可迭代对象==获取迭代器

    - 使用==生成器表达式==`(表达式 for 项 in 可迭代对象 if 条件)`创建==生成器==获取

        因为生成器==返回==一个迭代器

1. 检索迭代器

    使用`next()`函数获取下一个项

### 函数

0. 内置函数

     - `range()`函数创建一个可迭代对象，用于for循环
     - `len()`函数获取对象的长度
     - `setattr()`设置属性值
     - `isinstance()`判断一个对象是否属于某种类型

1. 高阶函数

    高阶函数是一个函数==构建器==，==返回骨架函数==

2. Lambda匿名函数

    - 基本用法
    
        `lambda arguments: expression`
    
    - 与`map()`结合使用
    
        `map()`函数将给定函数应用于可迭代对象的每个元素
    
    - 与`fliter()`结合使用
    
        函数返回True的元素被保留

### 模块

0. os模块——`import os`
      - `os.makedirs(dir,exist_ok=True)`创建多级目录
      - `os.path.join(dir,filename)`把目录和文件名合成一个路径
      - `os.path.dirname()`获取文件的目录
1. datatime模块——`from datatime import datatime`
    - `datatime.now()`获取当前时间
    - `.strftime('%Y-%m-%d_%H:%M:%S')`方法转换成==字符串==
2. yaml模块——`import yaml`
    - `yaml.safe_load()`读取yaml文件
    - `yaml.safe_dump()`将python字典或列表写入yaml文件
3. argparse模块
    - `argparse.ArgumentParser()`创建命令行参数解析对象
    - `argparse.add_argument()`创建命令行参数
    - `.parse_known_args()`解析命令行参数
4. tqdm模块
    - `with tqdm() as pabr:`创建进度条
    - `pabr.set_description()`设置进度条描述
    - `pabr.set_postfix()`设置进度条信息
5. Matplotlib模块
    - `plt.figure()`创建图像
    - `plt.plot()`绘制图像
    - `plt.xlabel(), plt.ylabel()`横纵坐标标签
    - `plt.legend()`显示注释

### 类

0. 构造方法

    定义组成类的部分，这些部分是该类的属性

1. 方法、_方法和__方法

    - _方法是==protectd方法==，只在==内部或子类==调用
    - __方法是==private方法==，只在==内部==调用

2. 静态方法

    可以从==类本身==调用

## Numpy基础

- 设置种子：``np.random.seed(42)`

### 数组

0. 创建数组

    - 生成随机数组

        - `np.random.rand(N,1)`

            创建给定形状的数组，服从$[0,1)$区间均匀分布

        - `np.random.randn(N,1)`

            创建给定形状的数组，服从标准正态分布

    - 创建等间距数组

        - `np.arange(N)`

            ==整数==步长时使用
    
0. 数组的维度操作

    - 维度拼接
    
        `np.stack(,axis)`沿==增加的新维度==axis拼接
    
        `np.concatenate()`沿==指定维度==拼接
    
    - 维度交换
    
        `np.transpose(,)`一次交换两个维度

### 数组的数学函数

0. 原地打乱数组：`np.random.shuffle()`

1. 数组求均值：`np.mean(data,axis)`

2. 花式索引：允许利用整数数组进行索引

## PyTorch基础

- 设置种子
    - `torch.manual_seed(42)`
    - `torch.backends.cudnn.deterministic = True`
    - `torch.backends.cudnn.benchmark = False`

### 张量

1. 创建张量

    - 使用`torch.tensor()`函数==创建==张量，默认数据类型是`torch.int64`。
    - 使用`torch.randn()`函数创建服从==标准正态分布==的张量

2. 张量的基本属性

    - `.ndim`属性获取==维数==
    - `.shape`属性获取==形状==
    - `.dtype`属性获取==数据类型==
    - `.device`属性获取==设备==类型
    - `.numel()`方法获取张量中==元素个数==

3. 张量的维度操作

    - `.view()`方法重塑张量

        改变张量的形状，会与原始张量==共享底层数据==。
        
    - 升维和降维

        - `.unsqueeze()`在指定维度位置添加一个大小为1的维度
        - `.squeeze()`移除大小为1的维度
        - 会与原始张量==共享底层数据==

4. 张量的复制

    - `.data`属性复制

        会与原始张量==共享底层数据==，并从计算图中==分离==，但==不安全==。

    - `.detach()`方法复制

        会与原始张量==共享底层数据==，并从计算图中==分离==，但==安全==。

    - `.clone()`方法复制

        会创建==新的副本==，不会从计算图中==分离==。

    *何为安全之说？*

    *==原地修改==参与梯度计算的张量是不被允许的，因为会破坏梯度。*

    *对于用`.detach()`复制会在原地修改时直接==报错==，所以是安全的；而用`.data`复制会根据原地修改后的值计算==错误的梯度==，且==不会报错==。*

5. 张量数据类型的转换

    - `.float()`方法将数据类型转换为`torch.float32`

6. 张量的数据结构类型转换

    - Numpy数组和PyTorch张量相互转换

        - `torch.as_tensor()`函数将**Numpy数组**转换成**PyTorch张量**

            会与原始Numpy数组==共享底层数据==。

        - `.numpy()`方法将**PyTorch张量**转换回**Numpy数组**
        
            会与原始张量==共享底层数据==。
        
    - PIL图像和PyTorch图像张量相互转换

        PIL图像形状是HWC，PyTorch张量形状是NCHW

        - `ToTensor()(PIL)`将**PIL图像**转换**PyTorch张量**
        - `ToPILImage()(tensor)`将**PyTorch张量**转换回**PIL图像**

7. 张量的设备分配

    - GPU的基本信息

        - `torch.cuda.is_available()`函数检查GPU是否可用
        - `torch.cuda.device_count()`函数查看GPU数量
        - `torch.cuda.get_device_name()`函数查看GPU型号

    - `torch.device()`定义设备

        ```python
        import torch
        device = torch.device('cuda:0' if torch.cuda.is_available() else 'cpu')
        ```

    - `.to()`将张量==发送==到指定的设备

    - `.cpu()`将**GPU张量**转为**CPU张量**

8. 张量的梯度

    - `.requires_grad`属性控制梯度的开关

        - 直接`.requires_grad`属性设置为True，表明有梯度

        - 用`.requires_grad_()`方法将属性设置为True

            ==下划线(__)结尾==的方法，表示在==原地==修改，会修改==底层数据==。

    - `.backward()`方法计算梯度

    - `.grad`属性查看梯度值

    - `.zero_()`方法将梯度归零

        因为PyTorch会==累积==梯度，需要在参数更新==之后==将梯度==归零==。

    - `torch.no_grad()`方法临时==禁用==梯度计算

        允许对张量执行常规Python操作，而==不会影响计算图==。

### 张量的数学函数

0. 最大最小值
      - `torch.argmax(,dim)`指定维上最大值索引
0. 批量矩阵乘法
    - `torch.bmm()`
    - `torch.matmul()`
0. `.all()`用来判断所有元素是否为True
0. `.masked_fill(mask)`可以使mask中为True的位置被替换为指定值

























































































































