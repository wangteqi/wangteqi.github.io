---
icon: fontawesome/brands/apple
tags:
    - system

---

> 2023.9.1
>
> 王特起

# macOS系统设置

## 抹盘重装

1. 重启后 ==按住== <kbd>command</kbd>+<kbd>R</kbd>，进入 `macOS` 恢复界面

    ![reinstall-1](./assets/macos/reinstall-1.jpeg)

2. 输入密码后，点击 `磁盘工具`

    ![reinstall-2](./assets/macos/reinstall-2.jpeg)

3. 进入磁盘工具后，点击左上角 `显示-->显示所有设备`

    ![reinstall-3](./assets/macos/reinstall-3.jpeg)

4. 点到 `容器disk3`，然后点击右上方的 ==抹掉==

    ![reinstall-4](./assets/macos/reinstall-4.jpeg)

5. 保持名称为 `Macintosh HD` 不变、格式为 `APFS` 不变，点击 ==抹掉==

    ![reinstall-5](./assets/macos/reinstall-5.jpeg)

6. 点击完成后，退回到 `macOS` 恢复界面，点击 ==重新安装==

    ![reinstall-6](./assets/macos/reinstall-6.jpeg)

## 开机设置

1. ==不要跳过iCloud登陆==

2. ==启用== 定位服务

    ![setup-1](./assets/macos/setup-1.jpeg)

3. ==取消== 与Apple共享Mac分析

    ![setup-2](./assets/macos/setup-2.jpeg)

4. 改进Siri与听写中选择 ==以后==

    ![setup-3](./assets/macos/setup-3.jpeg)

5. ==取消== 文件保险箱磁盘加密

    ![setup-4](./assets/macos/setup-4.jpeg)

## 桌面设置

### 系统偏好设置

1. 在 `辅助功能-->指针控制-->触控板选项` 勾选使用触控板进行拖移，拖移样式选择 ==三指拖移==

    ![desk-1](./assets/macos/desk-1.jpeg)

2. 控制中心的设置

    ![desk-2](./assets/macos/desk-2.jpeg)

    最终的菜单栏图标

    ![desk-3](./assets/macos/desk-3.jpeg)

3. 桌面与程序坞的设置

    ![desk-4](./assets/macos/desk-4.jpeg)

    同时设置 ==触发角==

    ![desk-5](./assets/macos/desk-5.jpeg)

4. 在 `触控板-->更多手势` 中设置App Expose为 ==四指向下轻扫==

    ![desk-6](./assets/macos/desk-6.jpeg)

### 访达偏好设置

1. 通用

    ![desk-7](./assets/macos/desk-7.jpeg)

2. 边栏

    ![desk-8](./assets/macos/desk-8.jpeg)

3. 高级

    ![desk-9](./assets/macos/desk-9.jpeg)

4. 快捷键

    - 显示文件路径：<kbd>option</kbd>+<kbd>command</kbd>+<kbd>P</kbd>
    - 显示隐藏文件：<kbd>shift</kbd>+<kbd>command</kbd>+<kbd>.</kbd>

### 启动台图标整理

![desk-10](./assets/macos/desk-10.jpeg)

![desk-11](./assets/macos/desk-11.jpeg)

## 软件设置

### Command Line Tools安装

```zsh
xcode-select --install
```

### Homebrew安装

[Homebrew安装参考文档](https://mirrors.ustc.edu.cn/help/brew.git.html)

1. 临时设置环境变量

    ```zsh
    export HOMEBREW_BREW_GIT_REMOTE="https://mirrors.ustc.edu.cn/brew.git"
    export HOMEBREW_BOTTLE_DOMAIN="https://mirrors.ustc.edu.cn/homebrew-bottles"
    export HOMEBREW_API_DOMAIN="https://mirrors.ustc.edu.cn/homebrew-bottles/api"
    ```

2. 运行安装脚本

    ```zsh
    /bin/bash -c "$(curl -fsSL https://mirrors.ustc.edu.cn/misc/brew-install.sh)"
    ```

3. 安装完成后 ==配置环境==

    ```zsh
    echo >> /Users/coco/.zprofile
    echo 'eval "$(/usr/local/bin/brew shellenv zsh)"' >> /Users/coco/.zprofile
    eval "$(/usr/local/bin/brew shellenv zsh)"
    ```

4. 可以查看 `.zprofile` 文件

    ```zsh
    # --------------- Homebrew ---------------
    eval "$(/usr/local/bin/brew shellenv zsh)"
    
    ```

5. 常用brew命令

    ```zsh
    # 更新 Homebrew 本身和软件仓库信息
    brew update
    # 查看哪些软件可以升级
    brew outdated
    #安装软件
    brew install --cask <name>
    # 升级软件
    brew upgrade <name>
    # 查看已安装的软件
    brew list
    # 清理旧版本和缓存
    brew cleanup
    ```

### Clash Verge安装

1. 使用Homebrew安装

    ```zsh
    brew install --cask clash-verge-rev
    ```

2. 配置Clash Verge

    - 导入订阅后，开启 ==系统代理==

    - 在 `设置-->托盘点击事件` 选择 ==显示托盘菜单==

        ![clash-verge](./assets/macos/clash-verge.jpeg)

    - 使用 ==轻量模式==
    
3. [ClashXPro下载地址](https://github.com/weimeng23/ClashX_Pro)，在 `配置-->托管配置-->管理` 中添加订阅

### Google Chrome安装

1. 使用Homebrew安装

    ```zsh
    brew install --cask google-chrome
    ```

2. 配置Chrome

    - 主题：Aura Theme
    - 插件：ghelper

### Typora安装

1. 使用Homebrew安装

    ```zsh
    brew install --cask typora
    ```

2. 配置Typora

    - 文件

        ![typora-1](./assets/macos/typora-1.jpeg)

    - 编辑器

        ![typora-2](./assets/macos/typora-2.jpeg)

    - 图像

        ![typora-3](./assets/macos/typora-3.jpeg)

    - Markdown

        ![typora-4](./assets/macos/typora-4.jpeg)

    - 导出

        ![typora-5](./assets/macos/typora-5.jpeg)

    - 外观

        ![typora-6](./assets/macos/typora-6.jpeg)

    - 通用

        ![typora-7](./assets/macos/typora-7.jpeg)

3. 主题配置

    - 字体

        [Maple Mono NF CN字体](https://github.com/subframe7536/maple-font/releases)，同时将其添加到字体册中

        [霞鹜文楷字体](https://github.com/lxgw/LxgwWenKai/releases)

    - 主题样式

        sky-paw.css和sky-paw-print.css(用于导出pdf)

        ```css
        /*
         * Sky Paw Theme for Typora
         * 风格：浅蓝背景、白色纸张、圆角卡片、柔和阴影、深色代码块。
         * 灵感：https://github.com/guokaigdg/animal-island-ui
         * 字体目录：
         *   sky-paw.css
         *   sky-paw-print.css（用于导出pdf）
         *   sky-paw/LXGWWenKai
         *   sky-paw/MapleMono-NF-CN
         */
        
        /* ==================== 01. 字体与主题变量 ==================== */
        @font-face {
            font-family: "LXGW WenKai";
            src: url("sky-paw/LXGWWenKai/LXGWWenKai-Regular.ttf") format("truetype");
            font-style: normal;
            font-weight: 400;
            font-display: swap;
        }
        
        @font-face {
            font-family: "LXGW WenKai";
            src: url("sky-paw/LXGWWenKai/LXGWWenKai-Medium.ttf") format("truetype");
            font-style: normal;
            font-weight: 500;
            font-display: swap;
        }
        
        @font-face {
            font-family: "MapleMono NF CN";
            src: url("sky-paw/MapleMono-NF-CN/MapleMono-NF-CN-Regular.ttf") format("truetype");
            font-style: normal;
            font-weight: 400;
            font-display: swap;
        }
        
        @font-face {
            font-family: "MapleMono NF CN";
            src: url("sky-paw/MapleMono-NF-CN/MapleMono-NF-CN-Bold.ttf") format("truetype");
            font-style: normal;
            font-weight: 700;
            font-display: swap;
        }
        
        @font-face {
            font-family: "MapleMono NF CN";
            src: url("sky-paw/MapleMono-NF-CN/MapleMono-NF-CN-Italic.ttf") format("truetype");
            font-style: italic;
            font-weight: 400;
            font-display: swap;
        }
        
        @font-face {
            font-family: "MapleMono NF CN";
            src: url("sky-paw/MapleMono-NF-CN/MapleMono-NF-CN-BoldItalic.ttf") format("truetype");
            font-style: italic;
            font-weight: 700;
            font-display: swap;
        }
        
        :root {
            --ai-primary: #74b9e6;
            --ai-primary-hover: #91c9ed;
            --ai-primary-active: #438fc4;
            --ai-primary-bg: #eaf6fd;
        
            --ai-text-main: #1f1f1f;
            --ai-text-body: #333;
            --ai-text-secondary: #718896;
            --ai-text-muted: #8296a3;
            --ai-text-disabled: #aebdc6;
        
            --ai-bg-app: #f3f8fb;
            --ai-bg-paper: #fff;
            --ai-bg-soft: #e8f2f8;
            --ai-bg-input: #f1f7fa;
            --ai-border-light: #b7ccd8;
            --ai-border-soft: #d1e0e8;
        
            --ai-success: #6fba2c;
            --ai-warning: #f2c66d;
            --ai-highlight-bg: #fff5c2;
            --ai-mark-text: #d63200;
            --ai-mark-bg: #fae3e9;
        
            --ai-shadow-button: #afc3ce;
            --ai-shadow-input: #c5d6df;
            --ai-shadow-card: 0 3px 10px rgb(53 91 115 / 10%);
            --ai-shadow-large: 0 8px 24px rgb(53 91 115 / 14%);
            --ai-shadow-deep: 0 4px 10px rgb(53 91 115 / 24%);
        
            /* 正文按钮：浅棕色配色 */
            --ai-button-bg: #f3e4cf;
            --ai-button-bg-hover: #f7ead8;
            --ai-button-bg-active: #ead6bc;
            --ai-button-border: #d8bfa0;
            --ai-button-border-hover: #c9a57c;
            --ai-button-text: #5f4630;
            --ai-button-text-hover: #4f3826;
            --ai-button-shadow: #c9ad89;
            --ai-button-shadow-soft: rgb(100 72 42 / 10%);
            --ai-button-shadow-hover: rgb(100 72 42 / 13%);
            --ai-button-shadow-active: rgb(100 72 42 / 8%);
            --ai-button-focus: rgb(201 165 124 / 40%);
        
            --ai-radius-sm: 12px;
            --ai-radius: 18px;
            --ai-radius-lg: 24px;
            --ai-radius-pill: 999px;
        
            --ai-transition-fast: 150ms cubic-bezier(0.4, 0, 0.2, 1);
            --ai-transition-normal: 200ms ease;
            --ai-font: "LXGW WenKai";
            --ai-mono: "MapleMono NF CN";
        
            --callout-note: #2563eb;
            --callout-note-bg: #2563eb1a;
            --callout-tip: #16a34a;
            --callout-tip-bg: #16a34a1a;
            --callout-important: #7c3aed;
            --callout-important-bg: #7c3aed1a;
            --callout-warning: #d97706;
            --callout-warning-bg: #d977061a;
            --callout-caution: #dc2626;
            --callout-caution-bg: #dc26261a;
        
            --ai-code-bg: #21252b; /* 顶部窗口栏 */
            --ai-code-editor-bg: #292d3e; /* 下方代码编辑区 */
            --ai-code-header-height: 34px;
            --ai-code-border: #343a46;
            --ai-code-text: #a6accd;
            --ai-code-muted: #676e95;
            --ai-code-selection: rgb(167 178 189 / 20%);
            --ai-code-cursor: #efb460;
            --ai-code-red: #fc625d;
            --ai-code-yellow: #fdbc40;
            --ai-code-green: #35cd4b;
            --ai-code-shadow: 0 10px 30px rgb(0 0 0 / 32%);
            --ai-code-line: rgb(166 172 205 / 24%);
            --ai-code-language: #0e82c2;
            --ai-code-focus-bg: rgb(255 255 255 / 6%);
        
            /* Mermaid 渲染结果：浅色圆角卡片 */
            --ai-diagram-bg: #faf9f6;
            --ai-diagram-border: #e7dfd2;
            --ai-diagram-shadow: 0 3px 12px rgb(92 74 45 / 10%);
        
            --code-blue: #82aaff;
            --code-cyan: #89ddff;
            --code-purple: #c792ea;
            --code-orange: #f78c6c;
            --code-red: #f07178;
            --code-yellow: #ffcb6b;
            --code-green: #c3e88d;
            --code-white: #eeffff;
            --code-type: #decb6b;
            --code-tag: #ff5370;
            --code-link: #aa759f;
        
            --source-em: #c97d1c;
            --source-string: #5a9e1e;
            --source-danger: #c94444;
            --source-number: #dba90e;
        }
        
        *,
        *::before,
        *::after {
            box-sizing: border-box;
        }
        
        /* ==================== 02. 页面与正文容器 ==================== */
        html {
            font-size: 16px;
        }
        
        html,
        body {
            background: var(--ai-bg-app);
            color: var(--ai-text-body);
            font-family: var(--ai-font);
            letter-spacing: 0.01em;
            -webkit-font-smoothing: antialiased;
            -moz-osx-font-smoothing: grayscale;
        }
        
        #write {
            max-width: 860px;
            margin: 20px auto 10px;
            padding: 5px 25px;
            background: var(--ai-bg-paper);
            border-radius: var(--ai-radius-lg);
            box-shadow: var(--ai-shadow-card);
            color: var(--ai-text-body);
            font-size: 1rem;
            line-height: 1.6;
            overflow-wrap: break-word;
        }
        
        #write > :first-child {
            margin-top: 0 !important;
        }
        
        /* ==================== 03. 标题 ==================== */
        #write :is(h1, h2, h3, h4, h5, h6) {
            color: var(--ai-text-main);
            font-family: var(--ai-font);
            font-weight: 500;
            letter-spacing: 0.02em;
            line-height: 1.35;
            scroll-margin-top: 1.5rem;
        }
        
        #write h1 {
            margin: 1.5em 0 0.8em;
            padding-bottom: 0.5em;
            font-size: 2.25em;
            font-weight: 500;
            line-height: 1.3;
            text-align: center;
        }
        
        #write h1::after {
            content: "";
            display: block;
            width: 110px;
            height: 8px;
            margin: 0.4em auto 0;
            background: linear-gradient(
                    to right,
                    var(--ai-primary) 0 40%,
                    var(--ai-warning) 40% 60%,
                    var(--ai-success) 60% 100%
            );
            border-radius: var(--ai-radius-pill);
            box-shadow: 0 2px var(--ai-shadow-input);
        }
        
        #write h2 {
            margin: 1.4em 0 0.7em;
            padding: 8px 0 8px 14px;
            background: linear-gradient(
                    to right,
                    var(--ai-primary),
                    var(--ai-primary-bg) 60%,
                    var(--ai-bg-soft) 80%,
                    transparent
            );
            border-left: 5px solid var(--ai-primary);
            box-shadow: 0 2px var(--ai-shadow-input);
            font-size: 1.7em;
        }
        
        #write h3 {
            margin: 1.3em 0 0.6em;
            padding: 4px 0 8px 14px;
            border-bottom: 2px dashed var(--ai-border-soft);
            border-left: 3px solid var(--ai-primary);
            font-size: 1.32em;
            font-weight: 500;
        }
        
        #write h4 {
            margin: 1.2em 0 0.5em;
            padding-bottom: 6px;
            background: linear-gradient(
                    to right,
                    var(--ai-primary) 0 36px,
                    transparent 36px
            ) 0 100% / 100% 3px no-repeat;
            color: var(--ai-primary-active);
            font-size: 1.15em;
        }
        
        #write h5 {
            width: fit-content;
            margin: 1.1em 0 0.4em;
            padding: 3px 14px;
            background: var(--ai-bg-soft);
            border: 2px solid var(--ai-border-soft);
            border-radius: var(--ai-radius-pill);
            font-size: 0.98em;
        }
        
        #write h6 {
            margin: 1em 0 0.3em;
            color: var(--ai-text-muted);
            font-size: 0.82em;
            letter-spacing: 2px;
            text-transform: uppercase;
        }
        
        /* ==================== 04. 正文、链接与列表 ==================== */
        #write p {
            margin: 0.55em 0;
            line-height: 1.7;
        }
        
        #write li > p {
            margin: 0.25em 0;
        }
        
        #write :is(strong, b) {
            color: var(--ai-text-main);
            font-weight: 500;
        }
        
        #write :is(em, i) {
            color: var(--ai-text-main);
            font-style: italic;
        }
        
        #write :is(del, s) {
            color: var(--ai-text-disabled);
        }
        
        #write :is(mark, :not(pre) > code, tt) {
            display: inline-block;
            vertical-align: baseline;
            transform-origin: center;
            transition: transform var(--ai-transition-normal), box-shadow var(--ai-transition-normal);
        }
        
        #write mark {
            margin: 0 1px;
            padding: 0 3px;
            background: var(--ai-mark-bg);
            border-radius: 0.6em;
            color: var(--ai-mark-text);
            line-height: 1.6;
        }
        
        #write :is(mark, :not(pre) > code, tt):hover {
            position: relative;
            z-index: 1;
            transform: scale(1.05);
            box-shadow: 0 1px 4px rgb(53 91 115 / 12%);
        }
        
        #write a {
            padding: 0 2px;
            border-bottom: 2px dotted var(--ai-primary);
            color: var(--ai-primary-active);
            text-decoration: none;
            text-decoration-skip-ink: auto;
            transition: color var(--ai-transition-normal),
            background-color var(--ai-transition-normal),
            border-color var(--ai-transition-normal);
        }
        
        #write a:hover {
            background: var(--ai-primary);
            border-bottom-color: transparent;
            border-radius: 5px;
            color: var(--ai-bg-paper);
        }
        
        
        /* 正文中的普通按钮：浅棕色背景与轻微立体阴影 */
        #write button {
            -webkit-appearance: none;
            appearance: none;
        
            margin: 0 2px;
            padding: 4px 12px;
        
            background: var(--ai-button-bg);
            border: 1px solid var(--ai-button-border);
            border-radius: 8px;
            box-shadow: 0 2px 0 var(--ai-button-shadow),
            0 4px 8px var(--ai-button-shadow-soft);
        
            color: var(--ai-button-text);
            font: 400 1em/1.4 var(--ai-font);
            cursor: pointer;
        
            transition: background-color var(--ai-transition-fast),
            border-color var(--ai-transition-fast),
            color var(--ai-transition-fast),
            box-shadow var(--ai-transition-fast),
            transform var(--ai-transition-fast);
        }
        
        #write button:hover {
            background: var(--ai-button-bg-hover);
            border-color: var(--ai-button-border-hover);
            color: var(--ai-button-text-hover);
            box-shadow: 0 3px 0 var(--ai-button-shadow),
            0 5px 10px var(--ai-button-shadow-hover);
            transform: translateY(-1px);
        }
        
        #write button:active {
            background: var(--ai-button-bg-active);
            box-shadow: 0 1px 0 var(--ai-button-shadow),
            0 2px 4px var(--ai-button-shadow-active);
            transform: translateY(1px);
        }
        
        #write button:focus-visible {
            outline: 3px solid var(--ai-button-focus);
            outline-offset: 2px;
        }
        
        :is(a, button, .btn, input, select, textarea):focus-visible {
            outline: 3px solid rgb(116 185 230 / 45%);
            outline-offset: 2px;
        }
        
        #write :is(ul, ol) {
            margin: 0.7em 0;
            padding-left: 1.8em;
        }
        
        #write li {
            margin: 0.25em 0;
        }
        
        #write ul > li::marker {
            color: var(--ai-primary);
        }
        
        #write ol > li::marker {
            color: var(--ai-primary-active);
            font-weight: 500;
        }
        
        #write .task-list {
            padding-left: 0;
        }
        
        #write .task-list-item {
            position: relative;
            margin: 0.45rem 0;
            padding-left: 2.1rem;
            list-style: none;
        }
        
        #write .task-list-item > input {
            position: absolute;
            top: 0.2em;
            left: 0;
            width: 1.3em;
            height: 1.3em;
            margin: 0;
            appearance: none;
            background: transparent;
            border: 2px solid var(--ai-primary);
            border-radius: 6px;
            cursor: pointer;
        }
        
        #write .task-list-item > input:checked {
            background: var(--ai-primary) url("data:image/svg+xml,%3Csvg viewBox='0 0 16 16' fill='none' xmlns='http://www.w3.org/2000/svg'%3E%3Cpath d='M3.5 8.5l3 3 6-6' stroke='%23fff' stroke-width='2' stroke-linecap='round' stroke-linejoin='round'/%3E%3C/svg%3E") center / contain no-repeat;
        }
        
        /* ==================== 05. 引用与 Callout ==================== */
        #write :is(blockquote, .md-alert) {
            margin: 1em 0;
            padding: 12px 20px;
            border-radius: var(--ai-radius);
            box-shadow: 0 3px var(--ai-shadow-input);
            color: var(--ai-text-body);
        }
        
        #write :is(blockquote, .md-alert) p {
            margin: 0.4em 0;
        }
        
        #write blockquote {
            background: var(--ai-bg-soft);
            border-left: 3px solid var(--ai-primary);
        }
        
        #write blockquote blockquote {
            background: rgb(255 255 255 / 45%);
            box-shadow: none;
        }
        
        #write .md-alert {
            --callout-color: var(--callout-note);
            --callout-bg: var(--callout-note-bg);
            background: var(--callout-bg);
            border: 0;
            border-left: 3px solid var(--callout-color);
        }
        
        #write .md-alert-tip {
            --callout-color: var(--callout-tip);
            --callout-bg: var(--callout-tip-bg);
        }
        
        #write .md-alert-important {
            --callout-color: var(--callout-important);
            --callout-bg: var(--callout-important-bg);
        }
        
        #write .md-alert-warning {
            --callout-color: var(--callout-warning);
            --callout-bg: var(--callout-warning-bg);
        }
        
        #write .md-alert-caution {
            --callout-color: var(--callout-caution);
            --callout-bg: var(--callout-caution-bg);
        }
        
        #write .md-alert .md-alert-text {
            margin: 0 0 0.4em;
            color: var(--callout-color);
            font-weight: 500;
            line-height: 1.2;
        }
        
        #write .md-alert .md-alert-text-container {
            color: var(--callout-color);
        }
        
        #write .md-alert .md-alert-text-container svg {
            fill: currentcolor;
        }
        
        /* ==================== 06. 行内代码与代码块 ==================== */
        /* Maple Mono 使用真实正体、粗体、斜体和粗斜体 */
        #write :is(:not(pre) > code, tt),
        #write .md-fences,
        #typora-source,
        #typora-source .CodeMirror {
            font-synthesis: none;
        }
        
        #write :is(:not(pre) > code, tt) {
            margin: 0 1px;
            padding: 1px 5px;
            background: var(--ai-primary-bg);
            border: 1px solid var(--ai-border-soft);
            border-radius: 5px;
            color: var(--ai-primary-active);
            font-family: var(--ai-mono);
            font-size: inherit;
            line-height: 1.4;
        }
        
        #write .md-fences {
            position: relative;
            margin: 1em 0;
            padding: var(--ai-code-header-height) 20px 8px;
            overflow: visible;
        
            /* 顶部为深灰窗口栏，下方为蓝紫色代码编辑区 */
            background: linear-gradient(
                    to bottom,
                    var(--ai-code-bg) 0 var(--ai-code-header-height),
                    var(--ai-code-editor-bg) var(--ai-code-header-height) 100%
            );
        
            border: 2px solid var(--ai-code-border);
            border-radius: var(--ai-radius);
            box-shadow: var(--ai-code-shadow);
            color: var(--ai-code-text);
            font-family: var(--ai-mono);
            font-size: 0.92em;
            line-height: 1.65;
            transition: box-shadow var(--ai-transition-normal);
        }
        
        #write .md-fences:hover {
            box-shadow: 0 12px 32px rgb(0 0 0 / 36%);
        }
        
        /* 普通代码块始终显示窗口按钮；Mermaid 仅在编辑源码时显示 */
        #write .md-fences:not([lang="mermaid"])::before,
        #write pre.md-fences[lang="mermaid"]:focus-within::before {
            content: "" !important;
            position: absolute;
            top: 12px;
            left: 16px;
            z-index: 10;
            width: 12px;
            height: 12px;
            background: var(--ai-code-red);
            border-radius: 50%;
            box-shadow: 20px 0 var(--ai-code-yellow),
            40px 0 var(--ai-code-green);
            pointer-events: none;
        }
        
        #write .md-fences :is(.code-tooltip, .code-tooltip-content) {
            width: auto !important;
            height: auto !important;
            margin: 0 !important;
            padding: 0 !important;
            background: transparent !important;
            border: 0 !important;
            box-shadow: none !important;
        }
        
        #write .md-fences .code-tooltip {
            position: absolute !important;
            inset: 7px 16px auto auto !important;
            z-index: 20 !important;
            transform: none !important;
        }
        
        #write .md-fences .ty-cm-lang-input {
            display: inline-block !important;
            width: 110px !important;
            min-width: 0 !important;
            height: 26px !important;
            margin: 0 !important;
            padding: 2px 8px !important;
            background: transparent !important;
            border: 0 !important;
            border-radius: 6px !important;
            box-shadow: none !important;
            outline: 0 !important;
            color: var(--ai-code-language) !important;
            font: 400 0.78rem/22px var(--ai-mono) !important;
            overflow: hidden !important;
            text-align: center !important;
            text-overflow: ellipsis !important;
            white-space: nowrap !important;
            transform: none !important;
        }
        
        #write .md-fences .ty-cm-lang-input:focus {
            background: var(--ai-code-focus-bg) !important;
            border: 1px solid rgb(53 205 75 / 35%) !important;
        }
        
        #write .md-fences code {
            display: inline;
            margin: 0;
            padding: 0;
            background: transparent;
            border: 0;
            border-radius: 0;
            box-shadow: none;
            color: inherit;
            font-size: 1em;
            line-height: inherit;
            transform: none;
        }
        
        #write .md-fences .CodeMirror {
            background: transparent !important;
            color: var(--ai-code-text) !important;
            font-family: var(--ai-mono) !important;
            line-height: 1.65;
        }
        
        #write .md-fences .CodeMirror-gutters {
            background: transparent !important;
            border-right: 2px dashed var(--ai-code-line) !important;
        }
        
        #write .md-fences .CodeMirror-linenumber {
            color: var(--ai-code-muted) !important;
        }
        
        #write .md-fences .CodeMirror-code > div {
            box-shadow: none;
        }
        
        #write .md-fences .CodeMirror-scroll {
            overflow-x: auto !important;
        }
        
        #write .md-fences .CodeMirror-cursor {
            border-left: 2px solid var(--ai-code-cursor) !important;
        }
        
        #write .md-fences .CodeMirror-selected {
            background: var(--ai-code-selection) !important;
        }
        
        #write .md-fences .CodeMirror-selectedtext {
            background: transparent !important;
            color: inherit !important;
        }
        
        #write .md-fences .CodeMirror-line::selection,
        #write .md-fences .CodeMirror-line span::selection {
            background: transparent !important;
        }
        
        /* 深色代码语法高亮 */
        #write .md-fences :is(
            .cm-header,
            .cm-header-1,
            .cm-header-2,
            .cm-header-3,
            .cm-header-4,
            .cm-header-5,
            .cm-header-6
        ) {
            color: var(--code-blue) !important;
            font-weight: 700;
        }
        
        #write .md-fences :is(
            .cm-formatting,
            .cm-formatting-header,
            .cm-formatting-list,
            .cm-formatting-quote,
            .cm-formatting-code,
            .cm-formatting-code-block,
            .cm-formatting-strong,
            .cm-formatting-em,
            .cm-formatting-link,
            .cm-formatting-link-string,
            .cm-formatting-image,
            .cm-operator,
            .cm-url
        ) {
            color: var(--code-cyan) !important;
        }
        
        #write .md-fences :is(.cm-formatting, [class*="cm-formatting-"]) {
            opacity: 0.9;
        }
        
        #write .md-fences :is(.cm-keyword, .cm-property, .cm-attribute) {
            color: var(--code-purple) !important;
        }
        
        #write .md-fences :is(.cm-atom, .cm-number) {
            color: var(--code-orange) !important;
        }
        
        #write .md-fences :is(.cm-variable, .cm-string-2) {
            color: var(--code-red) !important;
        }
        
        #write .md-fences :is(.cm-variable-2, .cm-strong) {
            color: var(--code-white) !important;
        }
        
        #write .md-fences :is(.cm-variable-3, .cm-type, .cm-qualifier) {
            color: var(--code-type) !important;
        }
        
        #write .md-fences :is(.cm-string, .cm-bracket) {
            color: var(--code-green) !important;
        }
        
        #write .md-fences .cm-def {
            color: var(--code-blue) !important;
            font-weight: 700;
        }
        
        #write .md-fences :is(.cm-builtin, .cm-meta, .cm-em) {
            color: var(--code-yellow) !important;
        }
        
        #write .md-fences :is(.cm-comment, .cm-quote) {
            color: var(--ai-code-muted) !important;
            font-style: italic;
        }
        
        #write .md-fences .cm-tag {
            color: var(--code-tag) !important;
        }
        
        #write .md-fences .cm-link {
            color: var(--code-link) !important;
        }
        
        #write .md-fences .cm-strong {
            font-weight: 700;
        }
        
        #write .md-fences .cm-em {
            font-style: italic;
        }
        
        #write .md-fences .cm-error {
            background: var(--code-tag) !important;
            color: var(--ai-bg-paper) !important;
        }
        
        #write .md-fences .CodeMirror-matchingbracket {
            color: var(--ai-bg-paper) !important;
            text-decoration: underline;
        }
        
        /* Mermaid：编辑器保持深色，预览区保持文档背景 */
        #write pre.md-fences[lang="mermaid"] {
            margin: 1em 0 !important;
            padding: 0 !important;
            overflow: visible !important;
            background: transparent !important;
            border: 0 !important;
            border-radius: 0 !important;
            box-shadow: none !important;
            color: inherit !important;
        }
        
        /* Mermaid 未进入源码编辑状态时，不显示窗口按钮 */
        #write pre.md-fences[lang="mermaid"]:not(:focus-within)::before {
            content: none !important;
        }
        
        #write pre.md-fences[lang="mermaid"] .CodeMirror {
            position: relative;
            margin: 0 0 12px !important;
            padding: 0 20px 8px !important;
            overflow: hidden !important;
        
            /*
             * Mermaid 不使用渐变绘制顶部栏。
             * 顶部深灰区域改为加厚上边框，避免背景延伸到第一行源码。
             */
            background: var(--ai-code-editor-bg) !important;
            background-image: none !important;
            border: 2px solid var(--ai-code-border) !important;
            border-top: var(--ai-code-header-height) solid var(--ai-code-bg) !important;
            border-radius: var(--ai-radius) !important;
            box-shadow: var(--ai-code-shadow) !important;
            color: var(--ai-code-text) !important;
        }
        
        /* 清除 Typora / CodeMirror 给 Mermaid 内层附加的深色背景 */
        #write pre.md-fences[lang="mermaid"] :is(
            .CodeMirror-scroll,
            .CodeMirror-sizer,
            .CodeMirror-lines,
            .CodeMirror-code,
            .CodeMirror-code > div,
            .CodeMirror-code > div > div,
            .CodeMirror-line,
            pre.CodeMirror-line,
            .CodeMirror-linebackground,
            .CodeMirror-activeline,
            .CodeMirror-activeline-background
        ) {
            background: transparent !important;
            background-color: transparent !important;
            background-image: none !important;
            box-shadow: none !important;
        }
        
        /* Mermaid 渲染结果：浅色圆角卡片 */
        #write pre.md-fences[lang="mermaid"] .md-diagram-panel {
            margin: 0 !important;
            padding: 24px 20px !important;
            overflow-x: auto;
            overflow-y: hidden;
            background: var(--ai-diagram-bg) !important;
            border: 1px solid var(--ai-diagram-border) !important;
            border-radius: var(--ai-radius) !important;
            box-shadow: var(--ai-diagram-shadow) !important;
        }
        
        /* Mermaid 图形在卡片中居中显示 */
        #write pre.md-fences[lang="mermaid"] .md-diagram-panel svg {
            display: block;
            max-width: 100%;
            height: auto;
            margin: 0 auto;
        }
        
        /* ==================== 07. 公式、分隔线、表格与图片 ==================== */
        #write :is(.MathJax, mjx-container) {
            color: var(--ai-text-main);
        }
        
        #write hr {
            width: 70%;
            height: 18px;
            margin: 2.4em auto;
            background: url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' viewBox='0 0 32 18'><ellipse cx='16' cy='13' rx='5' ry='3.8' fill='%2374b9e6'/><circle cx='9' cy='6' r='2.3' fill='%2374b9e6'/><circle cx='14' cy='3' r='2.3' fill='%2374b9e6'/><circle cx='19' cy='3' r='2.3' fill='%2374b9e6'/><circle cx='24' cy='6' r='2.3' fill='%2374b9e6'/></svg>") center / 80px 18px repeat-x;
            border: 0;
        }
        
        /* 正文表格：只命中表格本身的直接单元格，避免污染 Typora 表格工具栏 */
        #write table:not(.md-table-edit) {
            margin: 1.2em auto;
            border: 2px solid var(--ai-border-light);
            border-collapse: separate;
            border-spacing: 0;
            border-radius: var(--ai-radius);
            box-shadow: var(--ai-shadow-card);
        }
        
        #write table:not(.md-table-edit) > thead {
            background: var(--ai-primary);
        }
        
        #write table:not(.md-table-edit) > thead > tr > th:first-child {
            border-top-left-radius: calc(var(--ai-radius) - 2px);
        }
        
        #write table:not(.md-table-edit) > thead > tr > th:last-child {
            border-top-right-radius: calc(var(--ai-radius) - 2px);
        }
        
        #write table:not(.md-table-edit) > :is(thead, tbody, tfoot) > tr > :is(th, td) {
            padding: 10px 16px;
            text-align: left;
            vertical-align: top;
        }
        
        #write table:not(.md-table-edit) > thead > tr > th {
            border: 0;
            color: var(--ai-bg-paper);
            font-weight: 500;
            letter-spacing: 0.02em;
        }
        
        #write table:not(.md-table-edit) > tbody > tr > td {
            border-top: 2px dashed var(--ai-border-soft);
            color: var(--ai-text-body);
        }
        
        #write table:not(.md-table-edit) > tbody > tr:nth-child(even) > td {
            background: var(--ai-bg-soft);
        }
        
        #write table:not(.md-table-edit) > tbody > tr:hover > td {
            background: var(--ai-highlight-bg);
        }
        
        /* 保留最后一行单元格的底部圆角，避免斑马纹或悬停背景覆盖圆角 */
        #write table:not(.md-table-edit)
        > :is(tbody, tfoot):last-child
        > tr:last-child
        > :first-child {
            border-bottom-left-radius: calc(var(--ai-radius) - 2px);
        }
        
        #write table:not(.md-table-edit)
        > :is(tbody, tfoot):last-child
        > tr:last-child
        > :last-child {
            border-bottom-right-radius: calc(var(--ai-radius) - 2px);
        }
        
        #write table:not(.md-table-edit) > caption {
            margin-bottom: 0.6em;
            color: var(--ai-text-secondary);
            font-weight: 500;
            text-align: center;
        }
        
        /* Typora 表格编辑条：独立于正文表格与全局按钮样式 */
        #write .md-table-edit {
            background: var(--ai-bg-paper) !important;
            border: 1px solid var(--ai-border-light) !important;
            border-radius: 15px !important;
            box-shadow: 0 2px 4px rgb(53 91 115 / 16%),
            0 7px 18px rgb(53 91 115 / 14%) !important;
            color: var(--ai-text-body) !important;
        }
        
        /* 工具栏内部会使用 table/th，必须覆盖正文表格规则 */
        #write .md-table-edit table {
            width: auto;
            margin: 0;
            background: transparent;
            border: 0;
            border-collapse: collapse;
            border-radius: 0;
            box-shadow: none;
        }
        
        #write .md-table-edit :is(thead, tbody, tfoot, tr, th, td) {
            background: transparent !important;
            border: 0 !important;
            box-shadow: none !important;
        }
        
        #write .md-table-edit :is(th, td) {
            padding: 0 !important;
            color: inherit !important;
            font-weight: 400 !important;
            letter-spacing: normal !important;
            vertical-align: middle !important;
        }
        
        #write .md-table-edit :is(.btn, button) {
            min-width: 30px;
            margin: 0 3px;
            padding: 5px 8px;
            background: transparent !important;
            border: 0 !important;
            border-radius: 5px !important;
            box-shadow: none !important;
            color: var(--ai-text-body) !important;
            font-weight: 400;
            transform: none !important;
        }
        
        #write .md-table-edit :is(.btn, button):is(:hover, :focus, :active, .active) {
            background: var(--ai-primary-bg) !important;
            border: 0 !important;
            box-shadow: inset 0 -2px rgb(67 143 196 / 18%) !important;
            color: var(--ai-primary-active) !important;
            transform: none !important;
        }
        
        #write .md-table-edit .md-table-resize-popover {
            padding: 0;
            background: transparent;
            border: 0;
            box-shadow: none;
        }
        
        #write .md-table-edit .md-table-resize-popover .md-reset {
            background: var(--ai-bg-paper);
            border: 1px solid var(--ai-border-light);
            border-radius: var(--ai-radius-sm);
            box-shadow: var(--ai-shadow-large);
        }
        
        #write .table-figure {
            max-width: 100%;
            margin: 1.2em 0;
            overflow-x: auto;
            border-radius: var(--ai-radius);
            -webkit-overflow-scrolling: touch;
        }
        
        #write .table-figure > table,
        #write .table-figure > .md-table {
            min-width: 100%;
            margin: 0;
        }
        
        #write img:not(.emoji) {
            max-width: 100%;
            height: auto;
            border-radius: var(--ai-radius);
            box-shadow: var(--ai-shadow-deep);
        }
        
        #write p > img:not(.emoji):only-child {
            display: block;
            margin: 1em auto;
        }
        
        #write .md-footnote {
            padding: 1px 6px;
            background: var(--ai-primary-bg);
            border-radius: 6px;
            color: var(--ai-primary-active);
            font-weight: 500;
        }
        
        ::selection {
            background: var(--ai-highlight-bg);
            color: var(--ai-text-main);
        }
        
        #write .md-focus-container {
            outline: 0;
        }
        
        /* ==================== 08. 侧边栏与界面控件 ==================== */
        :is(
            .sidebar,
            #typora-sidebar,
            .sidebar-content,
            .sidebar-content-content,
            .sidebar-tabs
        ) {
            background: var(--ai-bg-app) !important;
            color: var(--ai-text-body) !important;
            font-family: var(--ai-font);
        }
        
        :is(.sidebar, #typora-sidebar) {
            border-right: 2px solid var(--ai-border-soft);
        }
        
        .sidebar-tabs .sidebar-tab {
            color: var(--ai-text-secondary);
        }
        
        .sidebar-tabs .sidebar-tab.active {
            border-bottom: 3px solid var(--ai-primary);
            color: var(--ai-primary-active);
        }
        
        :is(.outline-item, .file-list-item) {
            margin: 2px 6px;
            padding: 6px 10px;
            border-radius: var(--ai-radius-sm);
            color: var(--ai-text-body);
        }
        
        :is(.outline-item, .file-list-item):hover {
            background: var(--ai-bg-soft) !important;
            color: var(--ai-text-main) !important;
        }
        
        :is(.outline-active, .file-list-item-selected) {
            background: var(--ai-primary-bg) !important;
            color: var(--ai-primary-active) !important;
            font-weight: 500;
        }
        
        .searchpanel-search-option-btn {
            background: var(--ai-bg-input);
            border: 2px solid var(--ai-border-light);
            border-radius: var(--ai-radius-sm);
        }
        
        #typora-quick-open {
            background: var(--ai-bg-app) !important;
        }
        
        :is(
            #typora-quick-open-input,
            .searchpanel-search-input,
            input[type="text"]:not(.ty-cm-lang-input),
            input[type="search"]
        ) {
            padding: 6px 12px;
            background: var(--ai-bg-input);
            border: 2.5px solid var(--ai-border-light) !important;
            border-radius: var(--ai-radius);
            box-shadow: 0 3px var(--ai-shadow-input);
            color: var(--ai-text-body);
            transition: var(--ai-transition-fast);
        }
        
        :is(
            #typora-quick-open-input,
            .searchpanel-search-input,
            input[type="text"]:not(.ty-cm-lang-input),
            input[type="search"]
        ):focus {
            border-color: var(--ai-primary) !important;
            box-shadow: 0 3px var(--ai-primary-active);
            outline: 0;
        }
        
        :is(.btn, .export-item, .modal-footer button) {
            padding: 4px 12px;
            background: var(--ai-bg-paper);
            border: 2px solid var(--ai-border-light);
            border-radius: var(--ai-radius-sm);
            box-shadow: 0 3px var(--ai-shadow-button);
            color: var(--ai-text-main);
            font-weight: 500;
            transition: var(--ai-transition-fast);
        }
        
        :is(.btn, .export-item, .modal-footer button):hover {
            background: var(--ai-bg-soft);
            box-shadow: 0 4px var(--ai-shadow-button);
            transform: translateY(-1px);
        }
        
        :is(.btn, .export-item, .modal-footer button):active {
            box-shadow: 0 1px var(--ai-shadow-button);
            transform: translateY(2px);
        }
        
        :is(.btn-primary, .modal-footer button.primary) {
            background: var(--ai-primary);
            border-color: var(--ai-primary-active);
            box-shadow: 0 3px var(--ai-primary-active);
            color: var(--ai-bg-paper);
        }
        
        :is(.btn-primary, .modal-footer button.primary):hover {
            background: var(--ai-primary-hover);
            box-shadow: 0 4px var(--ai-primary-active);
        }
        
        
        /* Typora 查找／替换栏：仅消除通用主题的误影响，保留原生尺寸与布局 */
        #md-searchpanel {
            background: var(--ai-bg-app);
            border-bottom: 1px solid var(--ai-border-soft);
            box-shadow: 0 2px 6px rgb(53 91 115 / 8%);
            color: var(--ai-text-body);
            font-family: var(--ai-font);
        }
        
        /* 搜索输入框：使用紧凑内边距，避免整栏被撑大 */
        #md-searchpanel .searchpanel-search-input {
            padding: 2px 6px;
            background: var(--ai-bg-paper);
            border: 1px solid var(--ai-border-light) !important;
            border-radius: 6px;
            box-shadow: none !important;
            color: var(--ai-text-body);
        }
        
        #md-searchpanel .searchpanel-search-input:focus {
            border-color: var(--ai-primary) !important;
            box-shadow: 0 0 0 2px rgb(116 185 230 / 18%) !important;
            outline: 0;
        }
        
        /* 查找栏通用控件：清除全局按钮的立体样式 */
        #md-searchpanel :is(.btn, button) {
            padding: 0 4px;
            background: transparent !important;
            border: 0 !important;
            border-radius: 0;
            box-shadow: none !important;
            color: var(--ai-text-main);
            font-weight: 400;
            transform: none !important;
        }
        
        /* “查找”、上下箭头和关闭按钮：只改变文字颜色，不显示按钮背景 */
        #md-searchpanel :is(.btn, button):hover,
        #md-searchpanel :is(.btn, button):focus,
        #md-searchpanel :is(.btn, button):active {
            background: transparent !important;
            border: 0 !important;
            box-shadow: none !important;
            color: var(--ai-primary-active);
            transform: none !important;
        }
        
        /* Aa、全词、正则：保留小型圆形开关按钮 */
        #md-searchpanel .searchpanel-search-option-btn {
            display: inline-flex !important;
            flex: 0 0 20px !important;
            align-self: center;
            align-items: center;
            justify-content: center;
        
            width: 20px !important;
            min-width: 20px !important;
            max-width: 20px !important;
            height: 20px !important;
            min-height: 20px !important;
            max-height: 20px !important;
        
            margin: 0 1px;
            padding: 0 !important;
        
            background: transparent !important;
            border: 1px solid var(--ai-border-light) !important;
            border-radius: 50% !important;
            box-shadow: none !important;
        
            color: var(--ai-text-main);
            font-size: 12px !important;
            line-height: 1 !important;
            transform: none !important;
        }
        
        /* 选项按钮悬停和启用状态 */
        #md-searchpanel .searchpanel-search-option-btn:hover,
        #md-searchpanel .searchpanel-search-option-btn:focus,
        #md-searchpanel .searchpanel-search-option-btn.active {
            background: var(--ai-primary-bg) !important;
            border-color: var(--ai-primary) !important;
            color: var(--ai-primary-active) !important;
        }
        
        /* 缩小按钮内部图标 */
        #md-searchpanel .searchpanel-search-option-btn > * {
            font-size: 11px !important;
            transform: scale(0.8);
        }
        
        /* 上一个、下一个：保持纯图标，不添加分隔线或按钮外框 */
        #md-searchpanel .btn-group {
            background: transparent;
            border: 0;
            border-radius: 0;
            box-shadow: none !important;
        }
        
        #md-searchpanel .btn-group > :is(.btn, button) {
            padding: 0 8px;
            background: transparent !important;
            border: 0 !important;
            border-radius: 0;
            box-shadow: none !important;
        }
        
        #md-searchpanel .btn-group > :is(.btn, button) + :is(.btn, button) {
            border-left: 0 !important;
        }
        
        /* 关闭按钮：保持纯图标 */
        #md-searchpanel :is(
            #searchpanel-close,
            #searchpanel-close-btn,
            .searchpanel-close-btn
        ) {
            padding: 0 8px;
            background: transparent !important;
            border: 0 !important;
            border-radius: 0;
            box-shadow: none !important;
        }
        
        /* 纯图标控件悬停时仅改变颜色 */
        #md-searchpanel .btn-group > :is(.btn, button):hover,
        #md-searchpanel :is(
            #searchpanel-close,
            #searchpanel-close-btn,
            .searchpanel-close-btn
        ):hover {
            background: transparent !important;
            color: var(--ai-primary-active) !important;
        }
        
        /* ==================== 09. 状态栏与源码模式 ==================== */
        :is(footer, #footer) {
            background: var(--ai-bg-app);
            border-top: 2px dashed var(--ai-border-soft);
            color: var(--ai-text-secondary);
            font-family: var(--ai-font);
        }
        
        .footer-item-info {
            color: var(--ai-text-muted);
        }
        
        /* 源码模式：统一使用 Maple Mono，并固定字号、字重与行高 */
        #typora-source,
        #typora-source .CodeMirror {
            background: var(--ai-bg-paper) !important;
            color: var(--ai-text-body) !important;
        }
        
        #typora-source,
        #typora-source .CodeMirror,
        #typora-source .CodeMirror-lines,
        #typora-source .CodeMirror-line,
        #typora-source .CodeMirror-line span {
            font-family: var(--ai-mono) !important;
        }
        
        #typora-source .CodeMirror {
            font-size: 16px !important;
            font-weight: 400 !important;
            line-height: 1.7 !important;
            letter-spacing: 0.01em;
        }
        
        #typora-source .CodeMirror-cursor {
            border-left: 2px solid var(--ai-primary-active) !important;
        }
        
        /* 源码模式行号栏：融入白色编辑区域，避免形成贯穿全高的浅蓝侧栏 */
        #typora-source .CodeMirror-gutters {
            background: var(--ai-bg-paper) !important;
            border-right: 0 !important;
            box-shadow: none !important;
        }
        
        #typora-source .CodeMirror-linenumber {
            padding: 0 10px 0 6px;
            color: var(--ai-text-muted) !important;
            font-family: var(--ai-mono) !important;
            font-size: 14px !important;
            font-weight: 400;
        }
        
        #typora-source .CodeMirror-selected,
        #typora-source .CodeMirror-line::selection,
        #typora-source .CodeMirror-line ::selection {
            background: var(--ai-highlight-bg) !important;
        }
        
        #typora-source :is(
            .cm-header,
            .cm-header-1,
            .cm-header-2,
            .cm-header-3,
            .cm-header-4,
            .cm-header-5,
            .cm-header-6
        ) {
            color: var(--ai-text-main) !important;
            font-weight: 700;
        }
        
        #typora-source :is(
            .cm-formatting,
            .cm-formatting-header,
            .cm-formatting-list,
            .cm-formatting-quote,
            .cm-formatting-code,
            .cm-formatting-code-block
        ) {
            color: var(--ai-primary-active) !important;
            opacity: 0.9;
        }
        
        #typora-source :is(.cm-formatting-strong, .cm-strong) {
            color: var(--ai-text-main) !important;
            font-weight: 700;
        }
        
        #typora-source :is(.cm-formatting-em, .cm-em) {
            color: var(--source-em) !important;
            font-style: italic;
        }
        
        #typora-source :is(
            .cm-link,
            .cm-formatting-link,
            .cm-formatting-link-string,
            .cm-def
        ) {
            color: var(--ai-primary-active) !important;
        }
        
        #typora-source :is(.cm-url, .cm-quote) {
            color: var(--ai-text-secondary) !important;
        }
        
        #typora-source :is(.cm-quote, .cm-comment) {
            font-style: italic;
        }
        
        #typora-source .cm-comment {
            color: var(--ai-text-disabled) !important;
        }
        
        #typora-source .cm-meta {
            color: var(--ai-text-muted) !important;
        }
        
        #typora-source .cm-string {
            color: var(--source-string) !important;
        }
        
        #typora-source :is(.cm-tag, .cm-keyword) {
            color: var(--source-danger) !important;
        }
        
        #typora-source .cm-number {
            color: var(--source-number) !important;
        }
        
        #typora-source .cm-variable {
            color: var(--ai-text-body) !important;
        }
        
        /* ==================== 10. 弹窗、菜单与滚动条 ==================== */
        .popover-title {
            background: var(--ai-primary-bg);
            border-radius: var(--ai-radius-sm) var(--ai-radius-sm) 0 0;
            color: var(--ai-primary-active);
            font-weight: 500;
        }
        
        :is(.popover, .auto-suggest-container, .dropdown-menu, .modal-content) {
            background: var(--ai-bg-paper);
            border: 2px solid var(--ai-border-light);
            box-shadow: var(--ai-shadow-large);
            color: var(--ai-text-body);
        }
        
        :is(.popover, .auto-suggest-container, .dropdown-menu) {
            border-radius: var(--ai-radius);
        }
        
        .modal-content {
            border-radius: var(--ai-radius-lg);
        }
        
        .popover.bottom > .arrow::after {
            border-bottom-color: var(--ai-bg-paper);
        }
        
        .popover.top > .arrow::after {
            border-top-color: var(--ai-bg-paper);
        }
        
        .popover.left > .arrow::after {
            border-left-color: var(--ai-bg-paper);
        }
        
        .popover.right > .arrow::after {
            border-right-color: var(--ai-bg-paper);
        }
        
        :is(.tip, .tooltip) {
            background: var(--ai-text-main);
            border-radius: var(--ai-radius-sm);
            box-shadow: var(--ai-shadow-card);
            color: var(--ai-bg-paper);
            font-family: var(--ai-font);
        }
        
        .dropdown-menu > li > a {
            color: var(--ai-text-body);
        }
        
        .dropdown-menu > li > a:hover {
            background: var(--ai-primary-bg);
            color: var(--ai-primary-active);
        }
        
        ::-webkit-scrollbar {
            width: 10px;
            height: 10px;
        }
        
        ::-webkit-scrollbar-track {
            background: var(--ai-bg-app);
        }
        
        ::-webkit-scrollbar-thumb {
            background: var(--ai-border-light);
            border: 2px solid var(--ai-bg-app);
            border-radius: var(--ai-radius-pill);
        }
        
        ::-webkit-scrollbar-thumb:hover {
            background: var(--ai-primary);
        }
        
        /* ==================== 11. 响应式与可访问性 ==================== */
        @media screen and (max-width: 600px) {
            #write {
                margin: 0 auto;
                padding: 8px 18px;
                border-radius: 0;
                box-shadow: none;
            }
        }
        
        @media (prefers-reduced-motion: reduce) {
            *,
            *::before,
            *::after {
                scroll-behavior: auto !important;
                transition-duration: 0.01ms !important;
                animation-duration: 0.01ms !important;
                animation-iteration-count: 1 !important;
            }
        }
        
        /* ==================== 12. 打印与 PDF 导出 ==================== */
        /*
         * Typora 的“导出 PDF”不一定使用 print media。
         * 因此导出容器的白色背景必须写在 @media print 外部，
         * 否则仍会继承页面的浅蓝色应用背景。
         */
        body.typora-export,
        body.typora-export .typora-export-content,
        .typora-export,
        .typora-export-content {
            min-height: 100vh;
            background: #fff !important;
        }
        
        body.typora-export #write,
        .typora-export #write,
        .typora-export-content #write {
            background: #fff !important;
        }
        
        @page {
            background: #fff;
        }
        
        @media print {
            *,
            *::before,
            *::after {
                -webkit-print-color-adjust: exact;
                print-color-adjust: exact;
            }
        
            /* Typora 导出时会给 body 添加 .typora-export，并包裹
               .typora-export-content；这些区域也必须显式设为白色。 */
            html,
            body,
            body.typora-export,
            .typora-export,
            .typora-export-content,
            #write {
                background: #fff !important;
            }
        
            html,
            body,
            #write {
                font-family: var(--ai-font) !important;
            }
        
            #write {
                width: 100%;
                max-width: 100%;
                margin: 0;
                padding: 0;
                border-radius: 0;
                box-shadow: none;
                orphans: 3;
                widows: 3;
            }
        
            /* 打印正文保持 Regular */
            #write :is(
                p,
                li,
                td,
                blockquote,
                .md-alert,
                .md-alert .md-alert-text-container
            ) {
                font-weight: 400 !important;
            }
        
            /* 打印标题、表头、提示标题和粗体使用 Medium */
            #write :is(
                h1,
                h2,
                h3,
                h4,
                h5,
                h6,
                th,
                caption,
                .md-alert .md-alert-text,
                strong,
                b
            ) {
                font-weight: 500 !important;
            }
        
            /* 普通代码块、Mermaid 源码编辑器和行内代码使用等宽字体，
               避免影响 Mermaid 图形预览中的文字。 */
            #write .md-fences:not([lang="mermaid"]),
            #write .md-fences:not([lang="mermaid"]) *,
            #write pre.md-fences[lang="mermaid"] .CodeMirror,
            #write pre.md-fences[lang="mermaid"] .CodeMirror *,
            #write :not(pre) > code,
            #write tt {
                font-family: var(--ai-mono) !important;
                font-weight: 400 !important;
            }
        
            /* 打印代码中的粗体与斜体使用 Maple Mono 对应真实字形 */
            #write .md-fences :is(.cm-strong, .cm-def, .cm-header),
            #write pre.md-fences[lang="mermaid"] .CodeMirror :is(.cm-strong, .cm-def, .cm-header) {
                font-weight: 700 !important;
            }
        
            #write .md-fences :is(.cm-em, .cm-comment, .cm-quote),
            #write pre.md-fences[lang="mermaid"] .CodeMirror :is(.cm-em, .cm-comment, .cm-quote) {
                font-style: italic !important;
            }
        
            #write :is(.md-fences, pre, blockquote, table, img, .md-diagram-panel) {
                box-shadow: none !important;
            }
        
            /* Mermaid 源码编辑器原规则带有 !important，打印时需单独覆盖。 */
            #write pre.md-fences[lang="mermaid"] .CodeMirror {
                box-shadow: none !important;
            }
        
            #write :is(h1, h2, h3, h4, h5, h6) {
                break-after: avoid;
                page-break-after: avoid;
            }
        
            #write :is(img, blockquote, .md-alert) {
                break-inside: avoid;
                page-break-inside: avoid;
            }
        
            #write :is(.md-fences, table, .table-figure) {
                break-inside: auto;
                page-break-inside: auto;
            }
        
            #write .table-figure {
                overflow: visible;
            }
        
            #write thead {
                display: table-header-group;
            }
        
            #write tfoot {
                display: table-footer-group;
            }
        }
        
        /* ==================== 13. PDF 纯白手动兜底（默认关闭） ==================== */
        /*html,*/
        /*body,*/
        /*.typora-export,*/
        /*.typora-export-content,*/
        /*#write {*/
        /*    background: #fff !important;*/
        /*}*/
        
        /*#write {*/
        /*    border-radius: 0 !important;*/
        /*    box-shadow: none !important;*/
        /*}*/
        
        ```

4. [管理激活设备](https://store.typora.io/my)

### Zinit安装

1. 使用Homebrew安装

    ```zsh
    brew install zinit
    ```

2. 配置Zinit

    - 基础配置

        在 `.zshrc` 文件中添加基础功能

        ```zsh
        # --------------- Zinit ---------------
        source /usr/local/opt/zinit/zinit.zsh
        
        # --------------- Options ---------------
        setopt numeric_glob_sort
        
        # --------------- Keybindings ---------------
        bindkey -e
        
        # --------------- Completion / Plugins ---------------
        zinit light zsh-users/zsh-completions
        zinit snippet OMZP::git
        
        zstyle ':completion:*' menu select
        zstyle ':completion:*' matcher-list 'm:{a-zA-Z}={A-Za-z}'
        
        autoload -Uz compinit
        compinit
        zinit cdreplay -q
        
        # --------------- Autosuggestions ---------------
        zinit light zsh-users/zsh-autosuggestions
        
        # --------------- History ---------------
        HISTFILE="$HOME/.zsh_history"
        HISTSIZE=10000
        SAVEHIST=10000
        
        setopt share_history
        setopt hist_ignore_space
        setopt hist_ignore_all_dups
        setopt hist_find_no_dups
        
        # --------------- Syntax highlighting ---------------
        zinit light zsh-users/zsh-syntax-highlighting
        
        ```
    
    - 配置现代命令行工具
    
        安装 `eza` 用于增强目录和文件列表显示；安装 `bat` 用于增强文本文件查看
    
        - 使用Homebrew安装
    
            ```zsh
            brew install eza
            brew install bat
            ```
    
        - 在 `.zshrc` 文件中添加现代命令行工具
    
            ```zsh
            # --------------- Aliases ---------------
            alias ls='eza --icons --group-directories-first'
            alias ll='eza -l --icons --sort=name'
            alias lt='eza --tree --icons --level=2 --group-directories-first'
            alias cat='bat --paging=never --style=plain'
            ```
        
        > [!Caution]
        >
        > 所有配置 ==必须== 在代码高亮插件 `Syntax highlighting` ==之前== 添加
    

### Ghostty安装

1. 使用Homebrew安装

    ```zsh
    brew install --cask ghostty
    ```

2. 配置Ghostty，[图标](https://macosicons.com/zh)

    ```zsh
    # ============================================
    # Ghostty Terminal Configuration (macOS)
    # File: com.mitchellh.ghostty/config.ghostty
    # Reload: Cmd + Shift + ,
    # ============================================
    
    # --- 字体 ---
    font-family = "Maple Mono NF CN"
    font-size = 14
    font-thicken = true
    adjust-cell-height = 2
    
    # --- 图标 ---
    macos-icon = custom
    macos-custom-icon = /Users/coco/Library/Application Support/com.mitchellh.ghostty/app-icon.icns
    
    # --- 主题 --- 
    theme = Catppuccin Mocha
    window-theme = dark
    
    # --- 窗口外观 ---
    background-opacity = 0.85
    background-blur = 30
    window-padding-x = 10
    window-padding-y = 8
    window-save-state = always
    
    # --- 光标 ---
    cursor-style = bar
    cursor-style-blink = true
    cursor-opacity = 0.8
    
    # --- 鼠标与剪贴板 ---
    mouse-hide-while-typing = true
    copy-on-select = clipboard
    clipboard-paste-protection = true
    
    # --- 历史输出缓冲区，约 25 MB ---
    scrollback-limit = 25000000
    
    # ============================================
    # 快捷键
    # ============================================
    
    # --- 标签页 ---
    keybind = cmd+t=new_tab
    keybind = cmd+w=close_surface
    
    # --- 创建分屏 ---
    keybind = cmd+d=new_split:right
    keybind = cmd+shift+d=new_split:down
    
    
    # --- 分屏管理 ---
    keybind = cmd+shift+e=equalize_splits
    keybind = cmd+shift+f=toggle_split_zoom
    
    # --- 调整字号 ---
    keybind = cmd+plus=increase_font_size:1
    keybind = cmd+minus=decrease_font_size:1
    keybind = cmd+zero=reset_font_size
    
    # --- 重新加载配置 ---
    keybind = cmd+shift+comma=reload_config
    
    ```

3. 主题配置

    - 使用homebrew安装Starship

        ```zsh
        brew install starship
        ```

    - 配置Starship主题为Catppuccin Powerline

        ```zsh
        starship preset catppuccin-powerline -o ~/.config/starship.toml
        ```

    - Catppuccin Powerline样式文件

        ```toml
        # ============================================
        # File: ~/.config/starship.toml
        # ============================================
        "$schema" = 'https://starship.rs/config-schema.json'
        
        add_newline = false
        
        format = """
        [](red)\
        $os\
        $username\
        [](bg:peach fg:red)\
        $directory\
        [](bg:yellow fg:peach)\
        $git_branch\
        $git_status\
        [](fg:yellow bg:green)\
        $c\
        $rust\
        $golang\
        $nodejs\
        $bun\
        $php\
        $java\
        $kotlin\
        $haskell\
        $python\
        [](fg:green bg:sapphire)\
        $conda\
        [](fg:sapphire bg:lavender)\
        $time\
        [ ](fg:lavender)\
        $cmd_duration\
        $line_break\
        $character"""
        
        palette = 'catppuccin_mocha'
        
        [os]
        disabled = false
        style = "bg:red fg:crust"
        
        [os.symbols]
        Windows = ""
        Ubuntu = "󰕈"
        SUSE = ""
        Raspbian = "󰐿"
        Mint = "󰣭"
        Macos = "󰀵"
        Manjaro = ""
        Linux = "󰌽"
        Gentoo = "󰣨"
        Fedora = "󰣛"
        Alpine = ""
        Amazon = ""
        Android = ""
        AOSC = ""
        Arch = "󰣇"
        Artix = "󰣇"
        CentOS = ""
        Debian = "󰣚"
        Redhat = "󱄛"
        RedHatEnterprise = "󱄛"
        
        [username]
        show_always = true
        style_user = "bg:red fg:crust"
        style_root = "bg:red fg:crust"
        format = '[ $user]($style)'
        
        [directory]
        style = "bg:peach fg:crust"
        format = "[ $path ]($style)"
        truncation_length = 3
        truncation_symbol = "…/"
        
        [directory.substitutions]
        "Documents" = "󰈙 "
        "Downloads" = " "
        "Music" = "󰝚 "
        "Pictures" = " "
        "Developer" = "󰲋 "
        
        [git_branch]
        symbol = ""
        style = "bg:yellow"
        format = '[[ $symbol $branch ](fg:crust bg:yellow)]($style)'
        
        [git_status]
        style = "bg:yellow"
        format = '[[($all_status$ahead_behind )](fg:crust bg:yellow)]($style)'
        
        [nodejs]
        symbol = ""
        style = "bg:green"
        format = '[[ $symbol( $version) ](fg:crust bg:green)]($style)'
        
        [bun]
        symbol = ""
        style = "bg:green"
        format = '[[ $symbol( $version) ](fg:crust bg:green)]($style)'
        
        [c]
        symbol = " "
        style = "bg:green"
        format = '[[ $symbol( $version) ](fg:crust bg:green)]($style)'
        
        [rust]
        symbol = ""
        style = "bg:green"
        format = '[[ $symbol( $version) ](fg:crust bg:green)]($style)'
        
        [golang]
        symbol = ""
        style = "bg:green"
        format = '[[ $symbol( $version) ](fg:crust bg:green)]($style)'
        
        [php]
        symbol = ""
        style = "bg:green"
        format = '[[ $symbol( $version) ](fg:crust bg:green)]($style)'
        
        [java]
        symbol = " "
        style = "bg:green"
        format = '[[ $symbol( $version) ](fg:crust bg:green)]($style)'
        
        [kotlin]
        symbol = ""
        style = "bg:green"
        format = '[[ $symbol( $version) ](fg:crust bg:green)]($style)'
        
        [haskell]
        symbol = ""
        style = "bg:green"
        format = '[[ $symbol( $version) ](fg:crust bg:green)]($style)'
        
        [python]
        symbol = ""
        style = "bg:green"
        format = '[[ $symbol( $version)(\(#$virtualenv\)) ](fg:crust bg:green)]($style)'
        
        [docker_context]
        symbol = ""
        style = "bg:sapphire"
        format = '[[ $symbol( $context) ](fg:crust bg:sapphire)]($style)'
        
        [conda]
        symbol = "  "
        style = "fg:crust bg:sapphire"
        format = '[$symbol$environment ]($style)'
        ignore_base = false
        
        [time]
        disabled = false
        time_format = "%R"
        style = "bg:lavender"
        format = '[[  $time ](fg:crust bg:lavender)]($style)'
        
        [line_break]
        disabled = true
        
        [character]
        disabled = false
        success_symbol = '[❯](bold fg:green)'
        error_symbol = '[❯](bold fg:red)'
        vimcmd_symbol = '[❮](bold fg:green)'
        vimcmd_replace_one_symbol = '[❮](bold fg:lavender)'
        vimcmd_replace_symbol = '[❮](bold fg:lavender)'
        vimcmd_visual_symbol = '[❮](bold fg:yellow)'
        
        [cmd_duration]
        show_milliseconds = true
        format = " in $duration "
        style = "bg:lavender"
        disabled = false
        show_notifications = true
        min_time_to_notify = 45000
        
        [palettes.catppuccin_mocha]
        rosewater = "#f5e0dc"
        flamingo = "#f2cdcd"
        pink = "#f5c2e7"
        mauve = "#cba6f7"
        red = "#f38ba8"
        maroon = "#eba0ac"
        peach = "#fab387"
        yellow = "#f9e2af"
        green = "#a6e3a1"
        teal = "#94e2d5"
        sky = "#89dceb"
        sapphire = "#74c7ec"
        blue = "#89b4fa"
        lavender = "#b4befe"
        text = "#cdd6f4"
        subtext1 = "#bac2de"
        subtext0 = "#a6adc8"
        overlay2 = "#9399b2"
        overlay1 = "#7f849c"
        overlay0 = "#6c7086"
        surface2 = "#585b70"
        surface1 = "#45475a"
        surface0 = "#313244"
        base = "#1e1e2e"
        mantle = "#181825"
        crust = "#11111b"
        
        [palettes.catppuccin_frappe]
        rosewater = "#f2d5cf"
        flamingo = "#eebebe"
        pink = "#f4b8e4"
        mauve = "#ca9ee6"
        red = "#e78284"
        maroon = "#ea999c"
        peach = "#ef9f76"
        yellow = "#e5c890"
        green = "#a6d189"
        teal = "#81c8be"
        sky = "#99d1db"
        sapphire = "#85c1dc"
        blue = "#8caaee"
        lavender = "#babbf1"
        text = "#c6d0f5"
        subtext1 = "#b5bfe2"
        subtext0 = "#a5adce"
        overlay2 = "#949cbb"
        overlay1 = "#838ba7"
        overlay0 = "#737994"
        surface2 = "#626880"
        surface1 = "#51576d"
        surface0 = "#414559"
        base = "#303446"
        mantle = "#292c3c"
        crust = "#232634"
        
        [palettes.catppuccin_latte]
        rosewater = "#dc8a78"
        flamingo = "#dd7878"
        pink = "#ea76cb"
        mauve = "#8839ef"
        red = "#d20f39"
        maroon = "#e64553"
        peach = "#fe640b"
        yellow = "#df8e1d"
        green = "#40a02b"
        teal = "#179299"
        sky = "#04a5e5"
        sapphire = "#209fb5"
        blue = "#1e66f5"
        lavender = "#7287fd"
        text = "#4c4f69"
        subtext1 = "#5c5f77"
        subtext0 = "#6c6f85"
        overlay2 = "#7c7f93"
        overlay1 = "#8c8fa1"
        overlay0 = "#9ca0b0"
        surface2 = "#acb0be"
        surface1 = "#bcc0cc"
        surface0 = "#ccd0da"
        base = "#eff1f5"
        mantle = "#e6e9ef"
        crust = "#dce0e8"
        
        [palettes.catppuccin_macchiato]
        rosewater = "#f4dbd6"
        flamingo = "#f0c6c6"
        pink = "#f5bde6"
        mauve = "#c6a0f6"
        red = "#ed8796"
        maroon = "#ee99a0"
        peach = "#f5a97f"
        yellow = "#eed49f"
        green = "#a6da95"
        teal = "#8bd5ca"
        sky = "#91d7e3"
        sapphire = "#7dc4e4"
        blue = "#8aadf4"
        lavender = "#b7bdf8"
        text = "#cad3f5"
        subtext1 = "#b8c0e0"
        subtext0 = "#a5adcb"
        overlay2 = "#939ab7"
        overlay1 = "#8087a2"
        overlay0 = "#6e738d"
        surface2 = "#5b6078"
        surface1 = "#494d64"
        surface0 = "#363a4f"
        base = "#24273a"
        mantle = "#1e2030"
        crust = "#181926"
        
        ```
    
    - 在 `.zshrc` 文件中添加Starship
    
        ```zsh
        # --------------- Tools ---------------
        eval "$(starship init zsh)"
        ```

### Longshot安装

1. 在AppStore中安装

2. 配置Longshot

    - 通用

        ![longshot-1](./assets/macos/longshot-1.jpeg)

    - 截图

        - 工具条-->工具条项目

            ![longshot-2](./assets/macos/longshot-2.jpeg)

        - 行为-->历史选项

            ![longshot-3](./assets/macos/longshot-3.jpeg)

        - 输出-->手动保存-->文件名

            ![longshot-4](./assets/macos/longshot-4.jpeg)

    - 贴图--->历史选项

        ![longshot-5](./assets/macos/longshot-5.jpeg)

    - 快捷键

        - 截图快捷键：<kbd>option</kbd>+<kbd>A</kbd>
        - 贴图快捷键：<kbd>P</kbd>
        - 贴图工具条快捷键：<kbd>Space</kbd>
        - 退出快捷键：<kbd>Esc</kbd>

### Magnet安装

1. 在AppStore中安装

2. 配置Magnet

    - 基础配置

        ![Magnet-1](./assets/macos/magnet-1.jpeg)

    - 快捷键配置

        ![Magnet-2](./assets/macos/magnet-2.jpeg)

### Manico安装

1. 使用Homebrew安装

    ```zsh
    brew install --cask manico
    ```

2. 配置Manico

    - 通用

        ![manico-1](./assets/macos/manico-1.jpeg)

    - 高级

        ![manico-2](./assets/macos/manico-2.jpeg)

    - 配置-->自定义-->App，并设置快捷键

        ![manico-3](./assets/macos/manico-3.jpeg)

### VS Code安装

1. 使用Homebrew安装

    ```zsh
    brew install --cask visual-studio-code
    ```

2. 配置VS Code

    - 插件

        - 主题：Dracula Theme Official
        - 图标：vscode-icons-mac

        ![vscode-1](./assets/macos/vscode-1.jpeg)

    - 修改配置后 ==User== 的 `setting.json` 文件

        ```json
        {
            "workbench.colorTheme": "Dracula Theme",
            "workbench.iconTheme": "vscode-icons-mac",
            "editor.wordWrap": "on"
        }
        ```

        ![vscode-2](./assets/macos/vscode-2.jpeg)

    - 自定义快捷键

        - 新建文件：New File

            <kbd>command</kbd>+<kbd>N</kbd>

        - 新建文件夹：New Folder

            <kbd>shift</kbd>+<kbd>command</kbd>+<kbd>N</kbd>

        - 新建窗口：New Window

            <kbd>shift</kbd>+<kbd>option</kbd>+<kbd>command</kbd>+<kbd>N</kbd>

        - 修改配置后 ==User== 的 `keybindings.json` 文件

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

            ![vscode-3](./assets/macos/vscode-3.jpeg)

### xFormula安装

在AppStore中安装公式编辑器xFormual

### MacTex安装

1. 使用Homebrew安装

    ```zsh
    brew install --cask mactex-no-gui
    ```

2. MacTex在VScode中的配置

    - 在VS Code中安装Latex Workshop插件

        ![mactex](./assets/macos/mactex.jpeg)

    - ==Workspace== 中的 `.vscode/settings.json` 文件

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

### Miniforge安装

1. 使用Homebrew安装

    ```zsh
    brew install --cask miniforge
    ```

2. 配置环境

    ```zsh
    conda init "$(basename "${SHELL}")"
    ```

    可以在 `.zshrc` 文件中查看配置

    ```zsh
    # --------------- Miniforge ---------------
    # >>> conda initialize >>>
    # !! Contents within this block are managed by 'conda init' !!
    __conda_setup="$('/usr/local/Caskroom/miniforge/base/bin/conda' 'shell.zsh' 'hook' 2> /dev/null)"
    if [ $? -eq 0 ]; then
        eval "$__conda_setup"
    else
        if [ -f "/usr/local/Caskroom/miniforge/base/etc/profile.d/conda.sh" ]; then
            . "/usr/local/Caskroom/miniforge/base/etc/profile.d/conda.sh"
        else
            export PATH="/usr/local/Caskroom/miniforge/base/bin:$PATH"
        fi
    fi
    unset __conda_setup
    # <<< conda initialize <<<
    ```

3. 关闭Conda提示修饰符，由Starship统一显示Conda环境

    ```zsh
    conda config --set changeps1 false
    ```

    关闭 Conda 启动终端时自动进入 `base` 环境

    ```zsh
    conda config --set auto_activate false
    ```

    可以在 `.condarc` 文件中查看配置

    ```zsh
    channels:
      - conda-forge
    mirrored_channels:
      conda-forge:
        - https://conda.anaconda.org/conda-forge
        - https://prefix.dev/conda-forge
    
    changeps1: false
    auto_activate: false
    
    ```

4. conda常用命令

    ```zsh
    # 查看所有环境
    conda env list
    # 创建环境
    conda create -n <env_name> python=3.12
    # 激活环境
    conda activate <env_name>
    # 退出当前环境
    conda deactivate
    # 删除环境
    conda remove -n <env_name> --all
    ```

### Pycharm安装

1. 使用Homebrew安装

    ```zsh
    brew install --cask pycharm
    ```

2. 使用学校邮箱登陆激活Pycharm

    ![pycharm-1](./assets/macos/pycharm-1.jpeg)

3. 配置主题和字体

    - 安装Dracula Theme插件，然后在 `Appearance-->Theme` 中设置为Dracula Colorful

        ![pycharm-2](./assets/macos/pycharm-2.jpeg)

    - 在 `Editor-->Font` 中设置字体为 Maple Mono NF CN

4. 选择conda创建的虚拟环境

    ![pycharm-3](./assets/macos/pycharm-3.jpeg)

### Royal tsx安装

1. 使用Homebrew安装

    ```zsh
    brew install --cask royal-tsx
    ```

2. 配置Royal tsx

    - 安装两个插件

        - Terminal
        - File Transfer

        ![royaltsx-1](./assets/macos/royaltsx-1.jpeg)

    - 配置步骤

        1. 点击 `File-->New Document` 新建，保存名称为 seu-server

        2. 在Credentials文件夹上右击，找到 `Add-->Credential`，在Credential中设置 ==服务器的账号和密码==

            ![royaltsx-2](./assets/macos/royaltsx-2.jpeg)

        3. 在Connections文件夹上右击，找到 `Add-->Folder`，命名为Server-4090

            - 在Server-4090文件夹上右击，找到 `Add-->Terminal` 设置SSH

                - 在Terminal中设置 ==服务器的IP==

                    ![royaltsx-2](./assets/macos/royaltsx-3.jpeg)

                - 在Credentials中设置之前已经 ==创建好的账户==

                    ![royaltsx-3](./assets/macos/royaltsx-4.jpeg)

            - 在Server-4090文件夹上右击，找到 `Add-->File Transfer` 设置SFTP

                - 在File Transfer中设置 ==服务器的IP==

                    ![royaltsx-4](./assets/macos/royaltsx-5.jpeg)

                - 在Credentials中设置之前已经 ==创建好的账户==

                    ![royaltsx-5](./assets/macos/royaltsx-6.jpeg)

        4. 文档整体构成

            ![royaltsx-7](./assets/macos/royaltsx-7.jpeg)

### Office安装

1. 在校园网环境下，下载[Office2024](https://software.seu.edu.cn/soft/detail/56)，选择 ==自定义== 就可以根据需要安装

    ![office-1](./assets/macos/office-1.jpeg)

2. 激活Office

3. 主题选择彩色并关闭深色模式

    ![office-2](./assets/macos/office-2.jpeg)

### Zotero安装

1. 使用Homebrew安装

    ```zsh
    brew install --cask zotero
    ```

2. 配置Zotero

    - 在[插件商店](https://zotero-chinese.com/plugins/)找到下面两个插件

        - [Translate for Zotero](https://zotero-chinese.com/plugins/#search=Translate%20for%20Zotero)
        - [Ethereal Style](https://zotero-chinese.com/plugins/#search=Ethereal%20Style)

        ![zotero-1](./assets/macos/zotero-1.jpeg)

    - 取消文件同步

        ![zotero-2](./assets/macos/zotero-2.jpeg)

### Blip安装

1. 使用homebrew安装

    ```zsh
    brew install --cask blip
    ```

2. 配置Blip

    ![blip](./assets/macos/blip.jpeg)

### Keka安装

1. 使用Homebrew安装

    ```zsh
    brew install --cask keka
    ```

2. 配置Keka

    ![keka](./assets/macos/keka.jpeg)

### Tencent Lemon安装

1. 使用Homebrew安装

    ```zsh
    brew install --cask tencent-lemon
    ```

2. 配置Tencent Lemon

    ![tencentlemon](./assets/macos/tencentlemon.jpeg)

### Chatgpt安装

使用Homebrew安装

```zsh
brew install --cask chatgpt
```

### Codex CLI安装

使用Homebrew安装

```zsh
brew install --cask codex
```

### UV安装

1. 使用Homebrew安装

    ```zsh
    brew install uv
    ```
    
2. 可以在 `.zshrc` 文件中查看配置

    ```zsh
    # --------------- UV ---------------
    . "$HOME/.local/bin/env"
    ```

3. 常用UV命令

    ```zsh
    # 在项目文件夹里创建项目
    uv init ~/UV-Demo --bare --python 3.10 --pin-python
    
    # 添加依赖
    uv add <package_name>
    # 删除依赖
    uv remove <package_name>
    
    # 添加本地 editable 项目
    uv add --editable <path>
    # 删除本地项目依赖
    uv remove <project_name>
    
    # 添加开发依赖
    uv add --dev <tool_name>
    # 删除开发依赖
    uv remove --dev <tool_name>
    
    # 同步环境
    uv sync --python 3.10
    # 同步并启用当前项目的 extra
    uv sync --extra <extra_name>
    
    # 运行项目命令
    uv run <command>
    
    # 临时运行 CLI 工具
    uvx <tool>
    
    # 激活虚拟环境
    source .venv/bin/activate
    
    # 查看依赖树
    uv tree
    
    # 检查环境
    uv pip check
    ```







































