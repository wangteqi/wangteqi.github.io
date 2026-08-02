> 2026.8.1
>
> 王特起

# Ubuntu系统设置

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

        