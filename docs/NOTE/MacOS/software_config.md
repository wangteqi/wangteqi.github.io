# 软件安装流程

## 安装Google浏览器

- Google浏览器下载地址

	[Chrome](https://www.google.com/intl/zh-CN/chrome/)

- ghelper插件下载地址

	[Ghelper](https://ghelper.net/)

## 安装Command Line Tools

- 下载地址

	[Command Line Tools for Xcode 14.2](https://developer.apple.com/develop/)

- 步骤

	点击 ==Download==，然后输入自己的密码，进入页面后点击 ==More==，搜索Command Line Tools for Xcode 14.2

	注： ==Monterey适配的版本是14.2以下==

## 安装ClashX

- ClashX下载地址

	[ClashX增强版](https://github.com/WilliamStar007/ClashX-V2Ray-TopFreeProxy/blob/main/clash%E4%B8%AD%E6%96%87%E7%89%88.md)

- ClashX设置

	![ClashX_1](./assets/软件设置/ClashX/ClashX_1.png)

	在托管的配置文件里添加自己的订阅

	![ClashX_2](./assets/软件设置/ClashX/ClashX_2.png)

## Terminal的配置

- Oh My Zsh的配置

	- [安装Oh My Zsh](https://ohmyz.sh/#install)

	- 配置Oh My Zsh的主题

		```
		ZSH_THEME="agnoster"
		```

	- 配置Oh My Zsh的插件

		```
		plugins=(
		    git
		    z
		    zsh-autosuggestions
		    zsh-syntax-highlighting    
		)  
		```

		`git`和`z`是自带的插件。

		zsh-autosuggestions和zsh-syntax-highlighting是第三方插件需要自行安装，安装方法：

		对于[zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions/blob/master/INSTALL.md)

		```shell
		git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
		```

		对于[zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting/blob/master/INSTALL.md)

		```shell
		git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
		```

- 设置终端字体和主题

	- 字体链接

		[MonacoForPowerline.ttf](https://github.com/Zhengqbbb/MonacoForPowerline/blob/main/MonacoForPowerline.ttf)，将其添加到字体册中

	- 主题链接

		[Dracula](https://draculatheme.com/terminal)

	- 设置终端的描述文件

		点击左下角...，导入下载好的 ==Dracula.teminal==，更改字体

		![Terminal_1](./assets/软件设置/Terminal/Terminal_1.png)

	- 终端呈现的样式
	
		![Terminal_2](./assets/软件设置/Terminal/Terminal_2.png)

## Homebrew的安装

- [参考文档](https://mirrors.tuna.tsinghua.edu.cn/help/homebrew/)

	- 设置为清华源

		```shell
		export HOMEBREW_INSTALL_FROM_API=1
		export HOMEBREW_API_DOMAIN="https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles/api"
		export HOMEBREW_BOTTLE_DOMAIN="https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles"
		export HOMEBREW_BREW_GIT_REMOTE="https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/brew.git"
		export HOMEBREW_CORE_GIT_REMOTE="https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-core.git"
		```

	- 按顺序运行命令

		- 下载安装脚本

			```shell
			git clone --depth=1 https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/install.git brew-install
			```

		- 执行安装

			```shell
			/bin/bash brew-install/install.sh
			```

		- 安装完成后配置环境

			```shell
			(echo; echo 'eval "$(/usr/local/bin/brew shellenv)"') >> /Users/coco/.zprofile
			eval "$(/usr/local/bin/brew shellenv)"
			```

		- 删除安装包

			```shell
			rm -rf brew-install
			```

- 日常使用，可设置成清华源镜像

	```shell
	export HOMEBREW_API_DOMAIN="https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles/api"
	export HOMEBREW_BOTTLE_DOMAIN="https://mirrors.tuna.tsinghua.edu.cn/homebrew-bottles"
	export HOMEBREW_BREW_GIT_REMOTE="https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/brew.git"
	export HOMEBREW_CORE_GIT_REMOTE="https://mirrors.tuna.tsinghua.edu.cn/git/homebrew/homebrew-core.git"
	export HOMEBREW_PIP_INDEX_URL="https://pypi.tuna.tsinghua.edu.cn/simple"
	```

## Anaconda的安装

- 使用homebrew下载

	```shell
	brew install --cask anaconda
	```

- 配置环境

	```shell
	source /usr/local/anaconda3/bin/activate
	conda init zsh
	```

## Tencent Lemon的安装

- 使用homebrew下载

	```shell
	brew install --cask tencent-lemon
	```

- 偏好设置

	- 状态栏

		![TencentLemon_1](./assets/软件设置/TencentLemon/TencentLemon_1.png)

	- 开机启动项

		![TencentLemon_2](./assets/软件设置/TencentLemon/TencentLemon_2.png)

		![TencentLemon_3](./assets/软件设置/TencentLemon/TencentLemon_3.png)

## MacTeX的安装

- 使用homebrew安装(建议ClashX开启全局连接)

	```shell
	brew install --cask mactex-no-gui
	```

- MacTex在VScode中的使用

	- 安装Latex Workshop

		![MacTex_1](./assets/软件设置/VScode/MacTex_1.png)

	- Workspace中的 ==.vscode/settings.json== 文件

		```json
		{
		    "latex-workshop.latex.tools": [
		        {
		            "name": "xelatex",
		            "command": "xelatex",
		            "args": [
		                "-synctex=1",
		                "-interaction=nonstopmode",
		                "-file-line-error",
		                "-pdf",
		                "%DOC%"
		            ]
		        },
		        {
		            "name": "latexmk",
		            "command": "latexmk",
		            "args": [
		                "-synctex=1",
		                "-interaction=nonstopmode",
		                "-file-line-error",
		                "-pdf",
		                "%DOC%"
		            ]
		        },
		        {
		            "name": "pdflatex",
		            "command": "pdflatex",
		            "args": [
		                "-synctex=1",
		                "-interaction=nonstopmode",
		                "-file-line-error",
		                "%DOC%"
		            ]
		        },
		        {
		            "name": "bibtex",
		            "command": "bibtex",
		            "args": [
		                "%DOCFILE%"
		            ]
		        }
		    ],
		    "latex-workshop.latex.recipes": [
		        {
		            "name": "xelatex",
		            "tools": [
		                "xelatex"
		            ]
		        },
		        {
		            "name": "xelatex -> bibtex -> xelatex*2",
		            "tools": [
		                "xelatex",
		                "bibtex",
		                "xelatex",
		                "xelatex"
		            ]
		        },
		        {
		            "name": "bibtex -> xelatex*2",
		            "tools": [
		                "bibtex",
		                "xelatex",
		                "xelatex"
		            ]
		        }
		    ],
		}
		```

## Pycharm的安装

- 使用homebrew安装专业版

	```shell
	brew install --cask pycharm
	```

- Conda executable的设置

	![Pycharm_1](./assets/软件设置/Pycharm/Pycharm_1.png)

- 主题设置

	安装Dracula Theme插件，然后在Appearance设置为Dracula Colorful

	![Pycharm_2](./assets/软件设置/Pycharm/Pycharm_2.png)

## VScode的安装

- 使用homebrew安装

	```shell
	brew install --cask visual-studio-code
	```

- 偏好设置

	- 插件

		主题：Dracula Official

		图标：vscode-icons-mac

		![VScode_1](./assets/软件设置/VScode/VScode_1.png)

		点右上方漏斗一样的图标，找到 ==Modified==，可以查看修改的设置

		![VScode_2](./assets/软件设置/VScode/VScode_2.png)

		User的 ==settings.json==文件

		```json
		{
		    "workbench.colorTheme": "Dracula",
		    "workbench.iconTheme": "vscode-icons-mac",
		    "editor.wordWrap": "on"
		}
		```

	- 自定义快捷键

		新建文件：New File

		新建文件夹 ：New Folder

		新建窗口：New Window

		注：点击右上角...，找到 ==show User keybindings==，可以查看修改的快捷键

		![VScode_2](./assets/软件设置/VScode/VScode_2.png)

		User的 ==keybindings.json== 文件

		```json
		// Place your key bindings in this file to override the defaults
		[
		    {
		        "key": "cmd+n",
		        "command": "explorer.newFile"
		    },
		    {
		        "key": "shift+cmd+n",
		        "command": "explorer.newFolder"
		    },
		    {
		        "key": "shift+alt+cmd+n",
		        "command": "workbench.action.newWindow"
		    },
		    {
		        "key": "shift+cmd+n",
		        "command": "-workbench.action.newWindow"
		    }
		]
		```

## Royal tsx的安装

- 使用homebrew安装

	```shell
	brew install --cask royal-tsx
	```

- Royal tsx的配置

	1. 安装两个必备插件
	
		- Terminal
		- File Transfer
	
		![Royaltsx_1](./assets/软件设置/Royaltsx/Royaltsx_1.png)
	
	2. 新建一个Document（命名为server_config）
	
		- 在Credentials中，找到`Add Credential`
	
			- 在 ==Credential->Credential== 中设置服务器中个人账号和密码。
	
				![Royaltsx_2](./assets/软件设置/Royaltsx/Royaltsx_2.png)
	
		- 在Connections中新建一个文件夹（命名为Server-2080ti），找到`Add Terminal`设置SSH
	
			- 在 ==Teriminal->Terminal== 中设置服务器的IP
	
				![Royaltsx_3](./assets/软件设置/Royaltsx/Royaltsx_3.png)
	
			- 在 ==Common->Credentials== 中设置之前已经创建好的账户
	
				![Royaltsx_4](./assets/软件设置/Royaltsx/Royaltsx_4.png)
	
		- 在Connections中，找到`Add File Transfer`设置SFTP
	
			- 在 ==File Transfer->File Transfer== 中设置服务器的IP
	
				![Royaltsx_5](./assets/软件设置/Royaltsx/Royaltsx_5.png)
	
			- 在 ==Common->Credentials== 中设置之前已经创建好的账户
	
				![Royaltsx_6](./assets/软件设置/Royaltsx/Royaltsx_6.png)
	
	3. 文档整体构成
	
		![Royaltsx_7](./assets/软件设置/Royaltsx/Royaltsx_7.png)

## Typora的安装

- 使用homebrew安装

	```shell
	brew install --cask typora
	```

- Typora的配置

	1. 文件设置

		![Typora_1](./assets/软件设置/Typora/Typora_1.png)

	2. 编辑器设置

		![Typora_2](./assets/软件设置/Typora/Typora_2.png)

	3. 图像设置

		![Typora_3](./assets/软件设置/Typora/Typora_3.png)

	4. Markdown设置

		![Typora_4](./assets/软件设置/Typora/Typora_4.png)

	5. 导出设置

		![Typora_5](./assets/软件设置/Typora/Typora_5.png)

	6. 外观设置

		![Typora_6](./assets/软件设置/Typora/Typora_6.png)

	7. 通用设置

		![Typora_7](./assets/软件设置/Typora/Typora_7.png)

## Snipaste的安装

- 使用homebrew安装

	```shell
	brew install --cask snipaste
	```

- 偏好设置

	- 常规

		![Snipaste_1](./assets/软件设置/Snipaste/Snipaste_1.png)

	- 截屏

		![Snipaste_2](./assets/软件设置/Snipaste/Snipaste_2.png)

		![Snipaste_3](./assets/软件设置/Snipaste/Snipaste_3.png)

	- 控制

		![Snipaste_4](./assets/软件设置/Snipaste/Snipaste_4.png)

## App Store中软件安装

- xFormula

- Magnet

	![Magnet](./assets/软件设置/AppStore/Magnet.png)

- Manico

	- 通用

		![Manico_1](./assets/软件设置/AppStore/Manico_1.png)

	- 高级

		![Manico_2](./assets/软件设置/AppStore/Manico_2.png)

	- 外观

		![Manico_3](./assets/软件设置/AppStore/Manico_3.png)

	- 配置选择自定义->App，添加快捷键

		![Manico_4](./assets/软件设置/AppStore/Manico_4.png)

		![Manico_5](./assets/软件设置/AppStore/Manico_5.png)

## Easyconnect的安装

[学校VPN下载地址](https://vpn.seu.edu.cn/)

## Office的安装

在校园网环境下，下载[Office2021](https://nic.seu.edu.cn/fwzn/rjzbh/wrrjxz/Mac.htm)，选择 ==自定== 就可以根据需要安装



