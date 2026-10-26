---
icon: fontawesome/solid/cubes
tags:
  - deep-learning

---

> 2023.9.13
>
> 王特起

# 模型训练流程学习

## 虚拟环境

### 创建虚拟环境

```zsh
# conda创建虚拟环境
conda create -n dl-demo python=3.12
# 激活conda虚拟环境
conda activate dl-demo

# uv创建虚拟环境
uv init ~/DL-Demo --bare --python 3.12 --pin-python
# 激活uv虚拟环境
source .venv/bin/activate
```

### 相关包的安装

1. 安装PyTorch

    ```zsh
    # conda
    pip install torch==2.2.2 torchvision==0.17.2
    pip uninstall numpy
    pip install numpy==1.26.0
    
    # uv
    uv add torch==2.2.2 torchvision==0.17.2
    uv add numpy==1.26.0
    ```

2. 安装torchinfo

    ```zsh
    # conda
    pip install torchinfo
    
    # uv
    uv add torchinfo
    ```

3. 安装yaml

    ```zsh
    # conda
    pip install pyyaml
    
    # uv
    uv add pyyaml
    ```

4. 安装loguru

    ```zsh
    # conda
    pip install loguru
    
    # uv
    uv add loguru
    ```

5. 安装wandb

    ```zsh
    # conda
    pip install wandb
    
    # uv
    uv add wandb
    
    wandb login
    wandb login --relogin
    https://api.wandb.ai
    ```

6. 安装tqdm

    ```zsh
    # conda
    pip install tqdm
    
    # uv
    uv add tqdm
    ```

7. 安装Matplotlib

    ```zsh
    # conda
    pip install matplotlib
    
    # uv
    uv add matplotlib
    ```

## 数据

### 数据拆分

使用 `random_split()` 方法进行训练——验证 ==拆分==

```python
import numpy as np
from torch.utils.data import random_split

# ----------------------------------- data ----------------------------------
# 生成/拆分数据
def generate_data():
    # 生成
    true_w = 2
    true_b = 1
    n = 32
    x = np.random.rand(n, 1)
    epsilon = 0.1 * np.random.randn(n, 1)
    y = true_w * x + true_b + epsilon

    # 拆分
    ratio = 0.8
    idx = np.arange(n)
    train_idx, val_idx = random_split(idx, [int(n * ratio), n - int(n * ratio)])
    train_x, train_y = x[train_idx], y[train_idx]
    val_x, val_y = x[val_idx], y[val_idx]

    return train_x, train_y, val_x, val_y
```

### 数据处理

1. 标准化

    计算每个图像的每个通道的平均像素值和标准差

2. 使用 `torchvision.transforms` 进行数据 ==转换==

    - `ToTensor()`
    - `ToPILImage()`
    - `Resize()`
    - `CenterCrop()`
    - `Normalize()`
    - `Compose([])`

### Dataset类

创建 ==自定义== 数据集，需要继承Dataset类并 ==重写== 下面的三个方法

- `__init__(self)`

    定义特征、标签和数据转换

- `__getitem__(self,index)`

    对特征和标签进行转换，然后返回特征和标签的相应切片，即可以 ==按需== 加载数据集

- `__len__()`

    返回数据集的大小

```python
from torch.utils.data import Dataset

class CustomDataset(Dataset):
    def __init__(self, data_x, data_y, data_transform=None):
        self.data_x = data_x
        self.data_y = data_y
        self.data_transform = data_transform

    def __getitem__(self, index):
        # 切片
        x = self.data_x[index]
        y = self.data_y[index]
        # 转换
        if self.data_transform is not None:
            x = self.data_transform(x)
            y = self.data_transform(y)

        return x, y

    def __len__(self):
        # 数据集大小
        return len(self.data_x)

```

### DataLoader类

用来得到 ==小批量== 的数据集，并可以选择 ==打乱==

1. 检索小批量数据集

    使用 `next(iter())` 检索

2. 小批量数据集的设备分配

    使用 `.to()` 将小批量数据发送到设备

3. 自定义DataLoader

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

1. `__init__(self)` 定义构成模型的部分

    - `super().__init__()` 执行父类的初始化方法

    - 参数

        使用 `nn.Parameter()` 类定义模型参数

        ```python
        self.weight = nn.Parameter(torch.rand(10))
        ```

    - 子模块

        - 网络层

            使用 `nn.Linear()`，`nn.Conv2d()` 定义层

        - 模块容器

            - `nn.Sequential()`：按 ==顺序== 组织多个模块，并自动依次执行

            - `nn.ModuleList()`：以列表形式保存多个模块，==手动== 调用

                ```python
                self.layers = nn.ModuleList([nn.Linear(10, 10) for _ in range(3)])
                ```

    - 动态注册子模块

        使用 `self.add_module(name, module)` 通过名称注册子模块

        ```python
        self.add_module('fc2', nn.Linear(10, 5))
        ```

    - Buffer

        使用 `self.register_buffer(name, tensor)` 注册属于模型状态、但不参与梯度更新的张量

2. `forward(self,x)` 定义前向传递中的 ==步骤==

    指定输入数据如何经过各个子模块进行计算

```python
import torch.nn as nn

from torchinfo import summary


class CustomModel(nn.Module):
    def __init__(self, in_dim, out_dim):
        super().__init__()
        # 定义构成模型的部分
        self.fc = nn.Linear(in_dim, out_dim)

    def forward(self, x):
        # 执行前向传递计算
        out = self.fc(x)

        return out


if __name__ == "__main__":
    summary(CustomModel(1, 1), input_size=(1, 1))
```

### 模型的功能

1. 设备分配

    使用 `.to()` 将模型发送到 ==数据== 所在的同一设备上

2. 模式设置

    因为丢弃(dropout)等机制在训练和测试阶段具有 ==不同的行为==

    - `.train()` 方法用于 ==训练==
    - `.eval()` 方法用于 ==验证==

3. 前向传递

    使用 `model()` 进行前向传递

4. 模型参数的使用

    - `.parameters()` 方法检索 ==所有模型参数的迭代器==

        提供给优化器，用于参数更新

    - `.named_parameters()` 方法 ==也== 是检索所有模型参数的迭代器，

        会提供包含 ==参数当前值== 及其 ==名称== 的元组，用于检查特定的参数

        ```python
        for name, param in model.named_parameters():
            print(name, param)
        ```

    - 计算模型参数量

        ```python
        sum(p.numel() for p in model.parameters() if p.requires_grad)
        ```

5. 模型结构的查看

    - `.named_modules()` 方法获取 ==模型的层== 及其 ==名称==

    - 使用torchinfo包中的 `summary()` 函数查看参与梯度计算的 ==模型结构==，输入是模型和维度，输出是每层的 ==输出的形状== 和 ==参数量==

        ```python
        from torchinfo import summary
        summary(model, input_size=(1, 10))
        ```

6. 模型的保存和加载

    - `.state_dict()` 方法获取模型的状态字典，用于 ==保存==
    - `.load_state_dict()` 方法用于 ==加载== 模型的状态

## 损失

### 常用损失

0. 均方误差(MSE)损失

    - 定义损失函数

        使用 `nn.MSELoss()` 类定义MSE损失函数，接收要应用的简化方法

        ```python
        iport torch.nn as nn
        loss_fn = nn.MSELoss(reduction='mean')
        ```

    - 计算均方误差损失

        ```python
        loss = loss_fn(predictions, label)
        ```

    - 获取损失值

        使用 `.item()` 方法获取损失值，因为其可以处理 ==只有== 一个元素的 ==有梯度的标量==

### 自定义损失函数类

```python
import torch.nn as nn


class CustomLoss(nn.Module):
    def __init__(self):
        super().__init__()
        # 定义构成损失的部分
        self.mse_loss_fn = nn.MSELoss(reduction='mean')

    def forward(self, y_pred, y):
        # 总损失
        loss = self.mse_loss_fn(y_pred, y)

        return loss
```

## 优化器

### 常规使用

0. 定义优化器

    使用 `optim.SGD()` 类定义SGD优化器，优化器接收要更新的 ==参数==、使用的 ==学习率==

    ```python
    import torch.optim as optim
    optimizer = optim.SGD([b, w], lr=lr)
    ```

1. 更新参数

    使用 `.step()` 方法执行 ==更新==

2. 梯度归零

    使用 `.zero_grad()` 方法将梯度 ==归零==

3. 优化器的保存与加载

    `.state_dict()` 方法查看优化器的状态字典，用于 ==保存==

    `.load_state_dict()` 方法用于 ==加载== 优化器

### 自定义使用

不同层使用不同的学习率

```python
param_groups = [{'params': layer_1.parameters(), 'lr': lr_1},
                       {'params': layer_2.parameters(), 'lr': lr_2}]
optimizer = optim.SGD(param_groups,
                      lr=lr)
```

## 学习率调度器

### 周期学习率调度器

0. 定义周期学习率调度器

    ```python
    scheduler = optim.lr_scheduler.StepLR(optimizer, step_size, gamma)
    ```

1. 更新优化器的学习率

    `.step()` 方法更新，但要放在优化器的 `.step()` ==之后==

2. 获取学习率列表

    `.get_last_lr()` 得到 ==当前== 学习率

### 小批量学习率调度器

- `CyclicLR()` 调度器

## 训练技巧

### 训练循环

0. 训练步骤函数的高阶函数

    由于无论使用哪种模型、损失函数和优化器，梯度下降的步骤都是 ==相同==

    > [!Tip]
    >
    > 可以构建一个**高阶函数**，用于接收 ==模型、损失函数和优化器==，并返回 ==一个训练步骤函数==。**训练步骤函数**用于 ==接收特征和标签==，并返回 ==损失值==

1. 小批量训练内循环函数

    构建内循环函数来执行 ==小批量梯度下降==，用于接收 ==设备、小批量数据集和训练步骤函数==，返回 ==训练损失值==

### 验证循环

0. 验证步骤函数的高阶函数

    因为验证时 ==不进行反向传播和优化==，所以其**高阶函数**，只需要接收 ==模型和损失函数==，并返回 ==一个验证步骤函数==。**验证步骤函数**用于 ==接收特征和标签==，并返回 ==损失值==。

1. 小批量验证内循环函数

    验证时需要 ==禁用== 梯度计算，使用 `torch.no_grad()` 来 ==包裹== 小批量验证内循环函数

### 保存和恢复检查点

0. 保存检查点
    - 创建一个 ==字典== 来包含检查点的信息
        - 模型的状态字典
        - 优化器的状态字典
        - 损失
        - 周期
    - 使用 `torch.save(checkpoint,path)` 保存到文件
1. 恢复检查点
    - 使用 `torch.load(,map_location=device)` 加载检查点字典
    - `.load_stat_dict()` 加载模型和优化器的状态字典

### 训练类的实现

0. 构造方法

    - 用户指定的参数

        - 设备
        - 模型
        - 损失函数
        - 优化器

    - 可选配置项

        因为这些 ==不是== 模型的一部分，没有这些也可以。所以在创建时设置为 ==None==，在需要时再分配值

        - 训练数据加载器
        - 验证数据加载器
        - wanda的tracker
        - Loguru的logger

    - 需要跟踪的变量

        - 周期
        - 训练损失
        - 验证损失

    - 函数

        - 训练步骤函数
        - 验证步骤函数

1. 处理可选配置项的方法

    定义时需要为某些 ==可选的参数== 指定 ==默认值None==，让用户在调用该方法时可不提供参数

2. 外循环方法

    用于 ==周期== 训练

3. 步骤函数的高阶函数方法

    是 ==protected方法==，用于提供步骤函数

4. 小批量内循环函数方法

    是 ==protected方法==，用于内循环

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

    设置成 `sys.stderr`，将信息输出到标准错误流，避免和 ==标准输出冲突==

    ```python
        logger.add(sink=sys.stderr,
                   level='INFO',
                   colorize=True,
                   format='<green>{time:YYYYMMDD_HHmmss}</green> | '
                          '<level>{level}</level> | '
                          '<cyan>{message}</cyan>')
    ```

2. 添加文件输出

    设置成输出的文件

    ```python
        logger.add(sink=logger_log,
                   level='INFO',
                   encoding='utf-8',
                   format='{time:YYYYMMDD_HHmmss} | '
                          '{level} | '
                          '{message}')
    ```

3. 使用 `logger.info()` 记录日志

### wandb跟踪实验

0. 初始化wandb

     ```python
     import wandb
     
     # 初始化wandb
     tracker = wandb.init(dir=log_dir, project=project,
                              name=f"{datetime.now().strftime('%Y%m%d_%H%M%S')}")
     ```

1. `.log()` 方法记录记录损失和准确率

2. 使用 `.finish()` 方法关闭


## 训练流程

### 基础设置

0. 训练配置参数

     - 命令行参数

         用于确定 ==加载的配置参数文件==，以及 ==覆盖== 原有的配置参数

         ```zsh
         python3 main.py --lr=0.1 --device.cuda=cuda:0,cuda:1
         ```

     - 配置参数文件

         定义训练的配置参数

1. 可重复性

    ==设置种子== 来确保训练的可重复性

2. 设置日志

    - 设置logger
    - 设置tracker

```python
from utils.common import init_config, set_seed, set_logger, set_tracker

# ----------------------------------- basic ----------------------------------
# 基础设置
def basic_setup():
    # 初始化配置参数
    cfg = init_config(loaded_cfg='configs/custom_config.yaml')

    # 设置随机种子
    set_seed(cfg.seed)

    # 设置实验日志以及跟踪实验
    # loguru日志
    logger = set_logger(cfg.log_dir, cfg.project)
    # wandb实验跟踪
    tracker = set_tracker(cfg.log_dir, cfg.project)

    return cfg, logger, tracker
```

### 数据集设置

- 数据拆分
- 数据处理
- 自定义数据集
- 加载小批量数据集

```python
from utils.common import generate_data
import torch
from dataset.custom_dataset import CustomDataset
from torch.utils.data import DataLoader

# ----------------------------------- dataset ----------------------------------
# 数据集设置
def loader_setup(cfg):
    # 生成/拆分数据
    train_x, train_y, val_x, val_y = generate_data()

    # 创建数据集
    # 转换
    data_transform = lambda data: torch.as_tensor(data).float()
    # 自定义数据集
    train_dataset = CustomDataset(train_x, train_y, data_transform)
    val_dataset = CustomDataset(val_x, val_y, data_transform)

    # 创建数据集加载器
    # 加载方式
    # TODO
    # 自定义数据集加载器
    train_loader = DataLoader(train_dataset, batch_size=cfg.dataset.batch_size, shuffle=True)
    val_loader = DataLoader(val_dataset, batch_size=cfg.dataset.batch_size)

    return train_loader, val_loader
```

### 训练设置

- 定义设备
- 定义模型
- 定义损失函数
- 定义优化器

```python
from model.custom_model import CustomModel
from loss.custom_loss import CustomLoss
import torch.optim as optim

# ----------------------------------- train ----------------------------------
# 训练设置
def train_setup(cfg):
    # 创建设备
    device = torch.device(cfg.device.gpu[0] if torch.cuda.is_available() else cfg.device.cpu)

    # 创建模型
    model = CustomModel(in_dim=cfg.model.in_dim, out_dim=cfg.model.out_dim)

    # 创建损失函数
    loss_fn = CustomLoss()

    # 创建优化器
    # 不同层的学习率
    # TODO
    # 自定义优化器
    optimizer = optim.SGD(model.parameters(), lr=cfg.optimizer.lr)

    # 创建学习率调度器
    # TODO

    # 加载预训练模型
    # TODO

    return device, model, loss_fn, optimizer
```

### 训练器设置

0. 自定义训练器
1. 设置可选配置项
2. 训练循环

```python
from trainer.custom_trainer import CustomTrainer

def main():
    # 基础设置
    cfg, logger, tracker = basic_setup()

    # 数据集设置
    train_loader, val_loader = loader_setup(cfg)

    # 训练设置
    device, model, loss_fn, optimizer = train_setup(cfg)

    # 模型训练设置
    # 创建训练器
    trainer = CustomTrainer(device, model, loss_fn, optimizer)

    # 可选配置项
    trainer.set_components(train_loader, val_loader, logger, tracker)

    # 训练循环
    # 记录训练日志
    logger.info(f'Starting training {cfg.project}')
    # 开始训练
    trainer.train_loop(cfg.trainer.start_epoch,
                       cfg.trainer.n_epochs,
                       cfg.checkpoint.load_ckpt,
                       cfg.checkpoint.loaded_ckpt,
                       cfg.checkpoint.save_ckpt,
                       cfg.checkpoint.saved_ckpt_interval,
                       cfg.checkpoint.saved_ckpt_dir,
                       cfg.visualization.plot_loss)
```

### 训练结果可视化

损失可视化

```python
import matplotlib.pyplot as plt


def plot_losses(train_losses):
    plt.figure(figsize=(10, 4))
    plt.plot(train_losses, label='Train Loss', c='b')
    plt.yscale('log')
    plt.xlabel('Epochs')
    plt.ylabel('Loss')
    plt.legend()
    plt.tight_layout()
    plt.show()

```





























































