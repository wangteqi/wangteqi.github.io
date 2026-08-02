> 2026.6.23
>
> 王特起

# reBot Arm B601调试记录

## Ubuntu双系统

### 版本

- win11+Ubuntu 22.04.5 desktop amd64

### 安装

1. 划分磁盘

    - 点击管理，找到磁盘管理
    - 点击压缩卷，然后输入压缩空间量300G(307200MB)

2. 使用Rufus制作系统盘

    - 选择镜像文件
    - 选择分区类型GPT

3. 按F2进入BIOS关闭secure boot，并调整启动顺序

4. UEFI引导黑屏解决

    - 按E键编辑启动项参数，找到linux开头的这一行
    - 将三条短横线删除，并添加 ==nomodeset== 参数，按F10保存

5. Ubuntu安装时规划磁盘分区

    - efi：500MB
    - swap：10G
    - /：100G
    - /home：剩余空间
    - 引导器的设备选择 ==刚才分配的efi系统分区== 

6. 安装net-tools 

    ```shell
    # 更新软件源列表
    sudo apt update && sudo apt upgrade -y
    # 安装你需要的软件net-tools
    sudo apt install net-tools
    # 查看端口
    ifconfig
    ```

7. 安装openssh-server

    ```shell
    # 双系统
    sudo apt update
    sudo apt install openssh-server -y
    
    # 在mac终端ssh到ubuntu
    ssh wtq@10.209.2.200
    exit
    ```

8. 安装Git

    ```shell
    sudo apt update
    sudo apt install git -y
    ```

9. 安装中文输入法

    ```shell
    sudo apt update
    sudo apt install fcitx5 fcitx5-chinese-addons fcitx5-config-qt fcitx5-frontend-gtk3 fcitx5-frontend-qt5
    
    im-config -n fcitx5
    fcitx5-configtool
    sudo reboot
    ```

10. 安装clash

    ```shell
    sudo apt install ./Clash.Verge_2.5.1_amd64.deb
    ```

11. 安装typora

     ```shell
     sudo apt install ./typora_1.13.6_amd64.deb
     ```
    
12. 安装chrome

     ```shell
     sudo apt install ./google-chrome-stable_current_amd64.deb
     ```


### 卸载

1. 使用DiskGenius软件删除Ubuntu的esp分区，swap分区，/分区和/home分区，记得 ==保存更改==
2. 点击管理，找到磁盘管理，点击扩展卷
3. 在ESP(0)——EFI中删除整个Ubuntu目录，用于删除Ubuntu引导项

## Mac虚拟机设置

### 版本

- macOS 12.7.4
- VMware Fusion 13.5.2
- Ubuntu 22.04.5 server amd64

### 设置步骤

1. 下载VMware出现"Account verification is Pending. Please try after some time."问题

    解决方案：参考[VMware-download-helper](https://github.com/St7530/VMware-download-helper)

2. 下载[ubuntu 22.04.5 server amd64](https://releases.ubuntu.com/22.04/?_gl=1*1jvf8rd*_gcl_au*MTExNTY0Nzk5OC4xNzgxNjExOTky)

3. 在VMware Fusion中配置虚拟机

    - 设置虚拟机名称为`Ubuntu22045.vmwarevm`

    - 停用侧通道缓解

    - 设置硬盘大小为200G，同时在 ==Ubuntu终端==中进行配置

        ```shell
        # 查看当前磁盘、分区、LVM 和挂载情况
        lsblk
        # 扩展磁盘空间
        sudo pvresize /dev/sda3
        sudo lvextend -r -l +100%FREE /dev/mapper/ubuntu--vg-ubuntu--lv
        # 查看根目录 / 的实际可用容量
        df -h /
        ```

    - 设置USB为3.1，同时打开 ==Mac终端== 修改VMware Fusion 的 preferences 配置文件

        ```shell
        grep -q 'vusbcamera.passthrough' ~/Library/Preferences/VMware\ Fusion/preferences || echo 'vusbcamera.passthrough = "TRUE"' >> ~/Library/Preferences/VMware\ Fusion/preferences
        ```

4. 在虚拟机中安装ubuntu 22.04.5

    - 安装完成后使用`uname -a`查看

    - 安装net-tools

        ```shell
        # 更新软件源列表
        sudo apt update
        # 安装你需要的软件net-tools
        sudo apt install net-tools
        # 查看端口
        ifconfig
        ```

        这样就可以在 ==mac终端== 下使用ssh连接到虚拟机
    
        ```shell
        # 在mac终端ssh到虚拟机
        ssh wtq@172.16.99.128
        # 退出
        exit
        ```
    
    - 安装桌面版
    
        ```shell
        # 更新软件源列表，并升级当前系统中已经安装的软件包
        sudo apt update && sudo apt upgrade -y
        # 安装 Ubuntu 图形桌面环境
        sudo apt install ubuntu-desktop -y
        # 设置系统默认启动到图形界面
        sudo systemctl set-default graphical.target
        # 重启虚拟机，让桌面环境和启动设置生效
        sudo reboot
        ```
    
    - 安装VMware Tools
    
        ```shell
        # 更新软件源
        sudo apt update
        # 安装你需要的软件VMware Tools
        sudo apt install open-vm-tools open-vm-tools-desktop -y
        # 重启虚拟机
        sudo reboot
        ```
        
        
    

## 测试RealSense摄像头

### 摄像头用的螺丝

m3 * 12，m3*18，1/4云台

### 安装RealSense Viewer

```shell
sudo apt update
sudo apt install -y curl gnupg lsb-release apt-transport-https

sudo mkdir -p /etc/apt/keyrings

curl -sSf https://librealsense.realsenseai.com/Debian/librealsenseai.asc | \
gpg --dearmor | sudo tee /etc/apt/keyrings/librealsenseai.gpg > /dev/null

echo "deb [signed-by=/etc/apt/keyrings/librealsenseai.gpg] https://librealsense.realsenseai.com/Debian/apt-repo $(lsb_release -cs) main" | \
sudo tee /etc/apt/sources.list.d/librealsense.list

sudo apt update

sudo apt install -y librealsense2-dkms librealsense2-utils
```

### 使用Realsense Viewer

```shell
realsense-viewer
```

## 测试机械臂

### 版本

- Ubuntu22.04.5
- Python 3.10

### 安装Miniforge

```shell
# 进入当前用户的 home 目录
cd ~
# 从 conda-forge 的 GitHub 页面下载 Miniforge 安装脚本
wget "https://github.com/conda-forge/miniforge/releases/latest/download/Miniforge3-$(uname)-$(uname -m).sh"
# 运行刚下载的 Miniforge 安装脚本
bash Miniforge3-$(uname)-$(uname -m).sh
# 初始化 conda 到 bash 终端
~/miniforge3/bin/conda init bash
# 重新加载 ~/.bashrc
source ~/.bashrc
# 查看conda版本
conda --version
```

### 环境配置

```shell
# 创建 Python 3.10 版本虚拟环境
conda create -y -n rebot python=3.10
# 激活虚拟环境
conda activate rebot
# 安装 motorbridge
pip install motorbridge
```

### 测试机械臂

```shell
conda activate rebot
# 为串口配置 666 权限
sudo chmod 666 /dev/ttyACM*
# 查看实际端口号
ls /dev/ttyACM*
# 启动 MotorBridge
# 在Ubuntu浏览器中打开 https://motorbridge.github.io/motorbridge-studio/
motorbridge-gateway -- \
  --bind 127.0.0.1:9002 --vendor damiao --transport dm-serial \
  --serial-port /dev/ttyACM0 --serial-baud 921600 \
  --dt-ms 20
  
# 退出
Ctrl + C
```

## Lerobot平台

### 版本

- Ubuntu 22.04.5
- Python 3.10
- torch 2.7

### 安装Miniforge

参考[安装Miniforge](# 测试机械臂)

### 克隆Lerobot仓库

```shell
mkdir ~/rebot_lerobot
cd ~/rebot_lerobot
ssh -N -R 7890:127.0.0.1:7890 wtq@服务器IP
git clone https://github.com/Seeed-Projects/lerobot.git
ls
```

### 环境配置

```shell
cd ~/rebot_lerobot

# 创建 conda 环境（Python 3.10）
conda create -y -n lerobot python=3.10

# 激活环境
conda activate lerobot

# 安装 lerobot 主项目（可编辑模式）
pip install -e ./lerobot

# 添加依赖包
pip install lerobot-teleoperator-rebot-arm-102
pip install lerobot-robot-seeed-b601
pip install motorbridge

# 安装 ffmpeg
conda install ffmpeg -c conda-forge
conda install ffmpeg=7.1.1 -c conda-forge
# 检查是否支持 libsvtav1 编码器
ffmpeg -encoders | grep svtav1

# 检查torch
python3
import torch
print(torch.cuda.is_available())
exit()
```

### 校准leader臂

```shell
# 初次连接，可能会报找不到串口/dev/ttyACM0,此时因为brltty在占用该串口
sudo dmesg | grep ttyUSB
# 移除brltty
sudo apt remove brltty 
# 查看实际端口号
ls /dev/ttyUSB*

# 为串口配置 666 权限
sudo chmod 666 /dev/ttyUSB*

# 校准leader臂
# /home/wtq/.cache/huggingface/lerobot/calibration/teleoperators/rebot_arm_102_leader/rebot_arm_102_leader.json
lerobot-calibrate \
    --teleop.type=rebot_arm_102_leader \
    --teleop.port=/dev/ttyUSB0 \
    --teleop.id=rebot_arm_102_leader

# 校准完成后测试
python ./lerobot-teleoperator-rebot-arm-102/examples/read_raw_angles.py \
      --port /dev/ttyUSB0
```

### 校准follower臂

```shell
# 为串口配置 666 权限
sudo chmod 666 /dev/ttyACM* 
# 查看实际端口号
ls /dev/ttyACM*

# 校准follower臂
# /home/wtq/.cache/huggingface/lerobot/calibration/robots/seeed_b601_dm_follower/follower1.json
lerobot-calibrate \
    --robot.type=seeed_b601_dm_follower \
    --robot.port=/dev/ttyACM0 \
    --robot.id=follower1 \
    --robot.can_adapter=damiao
```

### 遥操作

```shell
# 为串口配置 666 权限
sudo chmod 666 /dev/ttyUSB*  
sudo chmod 666 /dev/ttyACM* 

# 运行遥操作
lerobot-teleoperate \
    --robot.type=seeed_b601_dm_follower \
    --robot.port=/dev/ttyACM0 \
    --robot.id=follower1 \
    --robot.can_adapter=damiao \
    --teleop.type=rebot_arm_102_leader \
    --teleop.port=/dev/ttyUSB0 \
    --teleop.id=rebot_arm_102_leader
    
    
# 退出
Ctrl + C
```

### 添加摄像头

```shell
# 切换到 Camera 分支
cd ~/rebot_lerobot/lerobot
git checkout DepthCameraSupport
git pull origin DepthCameraSupport
git branch --show-current

# 安装 RealSense
pip install -e ".[realsense]"

# 给予权限
sudo chmod a+rw /dev/bus/usb/*/*

# 检测相机
lerobot-find-cameras realsense

# 测试摄像头
lerobot-teleoperate \
    --robot.type=seeed_b601_dm_follower \
    --robot.port=/dev/ttyACM0 \
    --robot.id=follower1 \
    --robot.can_adapter=damiao \
    --robot.cameras='{
    d435i_color: {
      type: realsense_d435i_color,
      serial_number_or_name: "261222077804",
      width: 640,
      height: 480,
      fps: 30,
      color_mode: rgb,
      color_stream_format: rgb8,
      rotation: 0,
      warmup_s: 1
    },
    d435i_depth: {
      type: realsense_d435i_depth,
      serial_number_or_name: "261222077804",
      width: 640,
      height: 480,
      fps: 30,
      max_depth_m: 2.0,
      depth_alpha: 0.2,
      rotation: 0,
      warmup_s: 5
    },
    d405_color: {
      type: realsense_d405_color,
      serial_number_or_name: "260322279736",
      width: 640,
      height: 480,
      fps: 30,
      color_mode: rgb,
      color_stream_format: rgb8,
      rotation: 0,
      warmup_s: 1
    },
    d405_depth: {
      type: realsense_d405_depth,
      serial_number_or_name: "260322279736",
      width: 640,
      height: 480,
      fps: 30,
      depth_alpha: 0.03,
      rotation: 0,
      warmup_s: 5
    }
  }' \
    --teleop.type=rebot_arm_102_leader \
    --teleop.port=/dev/ttyUSB0 \
    --teleop.id=rebot_arm_102_leader \
    --display_data=true
```

### 数据集制作

```shell
lerobot-record \
    --robot.type=seeed_b601_dm_follower \
    --robot.port=/dev/ttyACM0 \
    --robot.id=follower1 \
    --robot.can_adapter=damiao \
    --robot.cameras="{     d435i_color: {
      type: realsense_d435i_color,
      serial_number_or_name: "261222077804",
      width: 640,
      height: 480,
      fps: 30,
      color_mode: rgb,
      color_stream_format: rgb8,
      rotation: 0,
      warmup_s: 1
    },
    d435i_depth: {
      type: realsense_d435i_depth,
      serial_number_or_name: "261222077804",
      width: 640,
      height: 480,
      fps: 30,
      max_depth_m: 2.0,
      depth_alpha: 0.2,
      rotation: 0,
      warmup_s: 5
    },
    d405_color: {
      type: realsense_d405_color,
      serial_number_or_name: "260322279736",
      width: 640,
      height: 480,
      fps: 30,
      color_mode: rgb,
      color_stream_format: rgb8,
      rotation: 0,
      warmup_s: 1
    },
    d405_depth: {
      type: realsense_d405_depth,
      serial_number_or_name: "260322279736",
      width: 640,
      height: 480,
      fps: 30,
      depth_alpha: 0.03,
      rotation: 0,
      warmup_s: 5
    }}" \
    --teleop.type=rebot_arm_102_leader \
    --teleop.port=/dev/ttyUSB0 \
    --teleop.id=rebot_arm_102_leader \
    --display_data=true \
    --dataset.repo_id=seeed_rebot_b601_dm/test \
    --dataset.num_episodes=5 \
    --dataset.single_task="Grab the black cube" \
    --dataset.push_to_hub=false \
    --dataset.episode_time_s=30 \
    --dataset.reset_time_s=30 
```



### 训练

```shell
CUDA_VISIBLE_DEVICES=0 lerobot-train \
  --dataset.repo_id=seeed_rebot_b601_dm/test \
  --policy.type=act \
  --output_dir=outputs/train/act_rebot_test \
  --job_name=act_rebot_test \
  --policy.device=cuda \
  --wandb.enable=false \
  --policy.push_to_hub=false \
  --batch_size=20 \
  --steps=300000 
```



### 测试

```shell
lerobot-record \
  --robot.type=seeed_b601_dm_follower \
  --robot.port=/dev/ttyACM0 \
  --robot.can_adapter=damiao \
  --robot.cameras='{
    d435i_color: {
      type: realsense_d435i_color,
      serial_number_or_name: "261222077804",
      width: 640,
      height: 480,
      fps: 30,
      color_mode: rgb,
      color_stream_format: rgb8,
      rotation: 0,
      warmup_s: 1
    },
    d435i_depth: {
      type: realsense_d435i_depth,
      serial_number_or_name: "261222077804",
      width: 640,
      height: 480,
      fps: 30,
      max_depth_m: 2.0,
      depth_alpha: 0.2,
      rotation: 0,
      warmup_s: 5
    },
    d405_color: {
      type: realsense_d405_color,
      serial_number_or_name: "260322279736",
      width: 640,
      height: 480,
      fps: 30,
      color_mode: rgb,
      color_stream_format: rgb8,
      rotation: 0,
      warmup_s: 1
    },
    d405_depth: {
      type: realsense_d405_depth,
      serial_number_or_name: "260322279736",
      width: 640,
      height: 480,
      fps: 30,
      depth_alpha: 0.03,
      rotation: 0,
      warmup_s: 5
    }
  }' \
  --robot.id=follower1 \
  --display_data=false \
  --dataset.repo_id=seeed/eval_test123 \
  --dataset.single_task="Put lego brick into the transparent box" \
  --policy.path=outputs/train/act_rebot_test/checkpoints/last/pretrained_model
```















































