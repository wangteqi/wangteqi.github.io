---
icon: fontawesome/solid/server
tags:
  - server
---

# 服务器的使用

## Linux服务器上安装Anaconda和Pytorch
- 重装Anaconda

	1. 删除个人文件夹中所有文件

		```shell
		# 显示所有文件
		ls -al
		# 删除可见文件
		rm -rf *
		# 删除隐藏文件
		rm -rf .*
		```

	2. 如果有权限，可以删除和新建个人文件夹（如果没有，可以跳过)

		```shell
		# 删除和新建文件夹
		cd ..
		sudo rm -rf wangteqi
		sudo mkdir wangteqi
		# 新建的文件夹属于root用户,需修改成个人文件夹的用户名和组名（不然没有上传文件的权限）,然后重开终端
		sudo chown wangteqi:wangteqi wangteqi
		# 在个人文件夹下面，把初始化文件重新添加到文件夹，然后重开终端
		cp -a /etc/skel/. ~
		```

- 安装Anaconda

	1. 把 ==Anaconda3-2024.02-1-Linux-x86_64.sh== 文件拖到服务器上的个人文件内，（[服务器配置教程](../MacOS/software_config.md)中的 ==Royal tsx的安装==）

	2. 执行安装命令

		- 使用bash安装

			```shell
			bash Anaconda3-2024.02-1-Linux-x86_64.sh
			
			# 出现继续的提示，按ENTER继续
			Please, press ENTER to continue
			>>>
			```

		- 阅读license(可以按<kbd>q</kbd>跳过)

			```shell
			# 跳过阅读license
			q
			
			# 出现接受的提示，输入yes继续
			Do you accept the license terms? [yes|no]
			>>> yes
			```

		- 安装路径的选择

			```shell
			# 出现选择安装路径的提示，按ENTER继续
			Anaconda3 will now be installed into this location:
			/home/wangteqi/anaconda3
			
			  - Press ENTER to confirm the location
			  - Press CTRL-C to abort the installation
			  - Or specify a different location below
			
			[/home/wangteqi/anaconda3] >>> 
			
			# 随后出现，等待安装完成
			[/home/wangteqi/anaconda3] >>>
			PREFIX=/home/wangteqi/anaconda3
			Unpacking payload ...
			```

		- 初始化conda

			```shell
			# 出现是否初始化的提示，输入yes
			You can undo this by running `conda init --reverse $SHELL`? [yes|no]
			[no] >>>
			```

			注：如果这一步选择 ==no==，需要在安装完成后手动初始化

			```shell
			source ~/anaconda3/bin/activate
			conda init
			```

		- 安装完成后，重开终端

			```shell
			# 安装完成后提示
			==> For changes to take effect, close and re-open your current shell. <==
			
			Thank you for installing Anaconda3!
			```

		- 检查conda是否安装成功

			```shell
			conda -V
			```

- 创建虚拟环境并安装Pytorch

	```shell
	# 创建虚拟环境
	conda create -n pytorch python=3.11
	# 激活虚拟环境
	conda activate pytorch
	# 安装对应的包(GPU)
	pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu121
	# 安装对应的包(CPU)
	pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cpu
	```

## Tmux的使用

主要防止终端意外关闭

注：==要在非虚拟环境下创建（因为base环境也是虚拟环境）==，不然Python的版本有问题（仅在tmux版本不适配时参考此方法）

```shell
# 新建一个tmux会话
conda deactivate
tmux new -s train
conda activate pytorch
# 退出tmux会话
tmux detach
# 重新进入tmux
tmux a -t train
# 关闭创建的tmux
tmux kill-session -t train
```

## Pycharm中服务器使用

1. 在Tools——Deployment——Configuration中

    添加SFTP，输入服务器名称ubuntu22045

2. 在Connection——SSH configuration中

    输入服务器地址，用户名，密码，点击test

    点击Autodetect找到根目录

3. 在Mappings中

    选择远程的项目路径

4. 远程debug

    在Perference——Project——Python Interpreter

    点击Add Interpreter 选择on SSH 

5. 在 Virtualenv Environment选择Existing

    输入which python找到解释器的地址

    映射地址要选择根目录
