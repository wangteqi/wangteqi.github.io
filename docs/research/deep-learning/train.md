> 王特起
>
> 2017.3.1

# 模型训练笔记

## Conda虚拟环境

- 创建并激活虚拟环境

    ```shell
    # 创建虚拟环境
    conda create -n dl_note
    # 激活虚拟环境
    conda activate dl_note
    ```

- 安装PyTorch

    ```shell
    pip3 install torch torchvision
    ```

- 安装torchinfo

    ```shell
    pip3 install torchinfo
    ```

- 安装loguru

    ```shell
    pip3 install loguru
    ```
    
- 安装TensorBoard

    ```shell
    pip3 install tensorboard
    ```
    
- 安装yaml

    ```shell
    pip3 install pyyaml
    ```
    
- 安装tqdm

    ```shell
    pip3 install tqdm
    ```
    
- 安装Matplotlib

    ```shell
    pip3 install matplotlib
    ```

## 数据

### 数据拆分

使用`random_split()`方法进行训练——验证==拆分==

### 数据处理

0. 标准化

    计算每个图像的每个通道的平均像素值和标准差

1. 使用`torchvision.transforms`进行数据==转换==

    - 基于PIL图像
        - `Resize()`
        - `CenterCrop()`
    - 基于张量
        - `Normalize()`
    - 组合转换
        - `Compose([])`

### Dataset类

用来组织数据，形成==数据集==。

0. 创建==自定义==数据集，需要继承Dataset类并==重写==下面的三个方法：

    - `__init__(self)`

        定义特征、标签和数据转换

    - `__getitem__(self,index)`

        对特征和标签进行转换，然后返回特征和标签的相应切片，即可以==按需==加载数据集。

    - `__len__()`

        返回数据集的大小

### DataLoader类

用来得到==小批量==的数据集，并可以选择==打乱==。

0. 检索小批量数据集

    使用`next(iter())`检索

1. 小批量数据集的设备分配

    使用`.to()`将小批量数据发送到设备

2. 自定义DataLoader

    - 使用`collate_fn`参数自定义批次创建
    
        比如打包序列
    
        ```python
        def pack_collate(batch):
            X = [item[0] for item in batch]
            Y = [item[1] for item in batch]
        
            X_packed = nn.utils.rnn.pack_sequence(X, enforce_sorted=False)
            return X_packed, torch.as_tensor(Y).view(-1, 1)
        ```

## 模型

### 自定义模型类

需要在自定义的模型类中，实现下面两个方法：

- `__init__(self)`

    定义构成模型的部分，主要包括模型参数和层

    - 自定义模型参数

        使用`nn.Parameter()`类定义模型的参数

    - 定义==内部模型==（也称为==层==）

        使用内置PyTorch模型类`nn.Liner()`等定义层

        - `.add_module()`方法可以==动态==创建层
        - 在`nn.Sequential()`序列模型中可以创建==顺序执行的层==

- `forward(self,x)`

    定义前向传递中的==步骤==

### 模型的功能

0. 设备分配

    使用`.to()`将模型发送到==数据==所在的同一设备上

1. 模式设置

    因为丢弃(dropout)等机制在训练和测试阶段具有==不同的行为==

    - `.train()`方法用于==训练==
    - `.eval()`方法用于==验证==

2. 前向传递

    使用`model()`进行前向传递

3. 模型参数的使用

    - `.parameters()`方法检索==所有模型参数的迭代器==

        提供给优化器，用于参数更新。

    - `.named_parameters()`方法==也==是检索所有模型参数的迭代器，

        会提供包含==参数当前值==及其==名称==的元组，用于检查特定的参数。
        
    - 计算模型参数量

        ```python
        sum(p.numel for p in model.parameters() if p.requires_grd)
        ```

4. 模型结构的查看

    - `.named_module()`方法获取==模型的层==及其==名称==

    - 使用`summary()`函数查看参与梯度计算的==模型结构==，每层的==输出的形状==和==参数量==

        ```python
        from torchinfo import summary
        summary(model,input_size)
        ```

5. 模型的保存和加载

    - `.state_dict()`方法获取模型的状态字典，用于==保存==
    - `.load_state_dict()`方法用于==加载==模型的状态

## 损失

### 常用损失

0. 均方误差(MSE)损失

    - 定义损失函数

        使用`nn.MSELoss()`类定义MSE损失函数，接收要应用的简化方法。

        ```python
        iport torch.nn as nn
        loss_fn = nn.MSELoss(reduction='mean')
        ```

    - 计算均方误差损失

        ```python
        loss = loss_fn(predictions, label)
        ```

    - 获取损失值

        使用`.item()`方法获取损失值，因为其可以处理==只有==一个元素的==有梯度的标量==。

### 自定义损失函数类

```python
import torch.nn as nn


class CustomLoss(nn.Module):
    def __init__(self):
        super(CustomLoss, self).__init__()
        self.mse_loss = nn.MSELoss(reduction='mean')

    def forward(self, y_pred, y):
        loss = self._custom_loss(y_pred, y)
        return loss

    def _custom_loss(self, y_pred, y):
        custom_loss = self.mse_loss(y_pred, y)
        return custom_loss
```

## 优化器

### 常规使用

0. 定义优化器

    使用`optim.SGD()`类定义SGD优化器，优化器接收要更新的==参数==、使用的==学习率==。

    ```python
    import torch.optim as optim
    optimizer = optim.SGD([b, w], lr=lr)
    ```

1. 更新参数

    使用`.step()`方法执行==更新==

2. 梯度归零

    使用`.zero_grad()`方法将梯度==归零==

3. 优化器的保存与加载

    `.state_dict()`方法查看优化器的状态字典，用于==保存==

    `.load_state_dict()`方法用于==加载==优化器

### 自定义使用

0. 自定义层的学习率

    ```python
    optimizer = optim.SGD([{'params': layer_1.parameters(), 'lr': lr_1},
                           {'params': layer_2.parameters(), 'lr': lr_2}],
                          lr=lr)
    ```

## 学习率调度器

### 周期学习率调度器

0. 定义周期学习率调度器

    ```python
    scheduler = optim.lr_scheduler.StepLR(optimizer, step_size, gamma)
    ```

1. 更新优化器的学习率

    `.step()`方法更新，但要放在优化器的`.step()`==之后==

2. 获取学习率列表

    `.get_last_lr()`得到==当前==学习率

### 小批量学习率调度器

- `CyclicLR()`调度器

## 训练技巧

### 训练循环

0. 训练步骤函数的高阶函数

    由于无论使用哪种模型、损失函数和优化器，梯度下降的步骤都是==相同==。

    可以构建一个**高阶函数**，用于接收==模型、损失函数和优化器==，并返回==一个训练步骤函数==。**训练步骤函数**用于==接收特征和标签==，并返回==损失值==。

1. 小批量训练内循环函数

    构建内循环函数来执行==小批量梯度下降==，用于接收==设备、小批量数据集和训练步骤函数==，返回==训练损失值==。

### 验证循环

0. 验证步骤函数的高阶函数

    因为验证时==不进行反向传播和优化==，所以其**高阶函数**，只需要接收==模型和损失函数==，并返回==一个验证步骤函数==。**验证步骤函数**用于==接收特征和标签==，并返回==损失值==。

1. 小批量验证内循环函数

    验证时需要==禁用==梯度计算，使用`torch.no_grad()`==包裹==小批量验证内循环函数

### 保存和恢复检查点

0. 保存检查点
    - 创建一个==字典==来包含检查点的信息
        - 模型的状态字典
        - 优化器的状态字典
        - 损失
        - 周期
    - 使用`torch.save(checkpoint,path)`保存到文件
1. 恢复检查点
    - 使用`torch.load(,map_location=device)`加载检查点字典
    - `.load_stat_dict()`加载模型和优化器的状态字典

### 训练类的实现

0. 构造方法
     - 用户指定的参数
         - 设备
         - 模型
         - 损失函数
         - 优化器
         
     - 占位符
       
         因为这些==不是==模型的一部分，没有这些也可以。所以在创建时设置为==None==，在需要时再分配值。
         
         - 训练数据加载器
         - 验证数据加载器
         - TensorBoard的writer
         - Loguru的logger
         
     - 需要跟踪的变量
         - 周期
         - 训练损失
         - 验证损失
         
     - 函数
         - 训练步骤函数
         - 验证步骤函数

1. 处理占位符的方法

    定义时需要为某些==可选的参数==指定==默认值None==，让用户在调用该方法时可不提供参数。

2. 外循环方法

    用于==周期==训练

3. 步骤函数的高阶函数方法

    是==protected方法==，用于提供步骤函数

4. 小批量内循环函数方法

    是==protected方法==，用于内循环

5. 保存和加载检查点方法

    用于保存、恢复检查点

## 训练日志

### Loguru文件日志

0. 移除handler

    因为默认是在控制台输出，所以先移除默认配置

    ```python
    from loguru import logger
    import sys
    logger.remove()
    ```

1. 添加控制台输出

    设置成`sys.stderr`，将信息输出到标准错误流，避免和==标准输出冲突==

    ```python
    logger.add(sink=sys.stderr,
               level='INFO',
               colorize=True,
               format='<green>{time:YYYY-MM-DD_HH:mm:ss}</green> | '
                      '<level>{level}</level> | '
                      '<cyan>{message}</cyan>')
    ```

2. 添加文件输出

    设置成输出的文件

    ```python
    logger.add(sink=logger_log,
               level='INFO',
               encoding='utf-8',
               format='{time:YYYY-MM-DD_HH:mm:ss} | '
                      '{level} | '
                      '{message}')
    ```

3. 使用`logger.info()`记录日志

### TensorBoard可视化日志

0. 创建SummaryWriter

    ```python
    from torch.utils.tensorboard import SummaryWriter
    writer = SummaryWriter(writer_log)
    ```

1. `.add_scalars(main_tag,tag_scalar_dict,global_step)`方法记录标量值

    记录损失和准确率

2. 使用`.close()`方法关闭

3. 命令行运行TensorBoard

    ```shell
    tensorboard --log_dir=writer_log
    ```


## 训练流程

### 基础设置

0. 训练配置参数

    - 命令行参数

        用于确定==加载的配置参数文件==，以及==覆盖==原有的配置参数

    - 配置参数文件

        定义训练的配置参数

1. 可重复性

    ==设置种子==来确保训练的可重复性

2. 设置日志

    - 设置logger
    - 设置writer

### 数据集设置

- 数据拆分
- 数据处理
- 自定义数据集
- 加载小批量数据集

### 训练设置

- 定义设备
- 定义模型
- 定义损失函数
- 定义优化器

### 训练器设置

0. 自定义训练器
1. 设置占位符参数
2. 周期设置
3. 恢复检查点
4. 开始训练
5. 保存检查点

### 训练结果可视化

0. 损失可视化

























































































































