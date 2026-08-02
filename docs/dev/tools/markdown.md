>2024.10.28
>
>王特起

# Markdown 基础

## 标题

方法：1～6个<kbd>#</kbd>+<kbd>空格</kbd>+Text

```
# 一级标题
## 二级标题
...
###### 六级标题
```

## 强调

### 加粗

方法：<kbd>\**</kbd>+Text+<kbd>**</kbd>

```
未加粗**文字加粗** 
```

未加粗**文字加粗**

### 斜体

方法：<kbd>\*</kbd>+Text+<kbd>*</kbd>

```
*文字斜体*
```

*文字斜体*

### 删除

方法：<kbd>\~\~</kbd>+Text+<kbd>~~</kbd>

```
~~删除的文字~~
```

~~删除的文字~~

### 高亮

方法：<kbd>\==</kbd>+Text+<kbd>==</kbd>

```
==高亮文字==
```

==高亮文字==

## 列表

### 无序列表

方法：<kbd>-</kbd>+<kbd>空格</kbd>+Text

```
- 列表1
- 列表2
	- 列表3
	- 列表4
		- 列表5
```

- 列表1

- 列表2
  - 列表3
  - 列表4
  	- 列表5

### 有序列表

方法：<kbd>数字.</kbd>+<kbd>空格</kbd>+Text

```
1. 有序列表1
2. 有序列表2
	1. 有序列表3
	2. 有序列表4
```

1. 有序列表1
2. 有序列表2
	1. 有序列表3
	2. 有序列表4

### 任务列表

方法：<kbd>-</kbd>+<kbd>空格</kbd>+<kbd>[空格或x]</kbd>+<kbd>空格</kbd>+Text

```
- [ ] 计划未完成
- [x] 计划完成
```

- [ ] 计划未完成

- [x] 计划完成

## 链接

### 网址/文档链接

方法：<kbd>[Text]</kbd>+<kbd>(url)</kbd>或者<kbd><</kbd>+url+<kbd>></kbd>

```
[百度](https://www.baidu.com )
<www.baidu.com>
[帮助文档](./help.md)
```

[百度](https://www.baidu.com )

<www.baidu.com>

### 图片链接

方法：<kbd>![Text]</kbd>+<kbd>(图片相对路径)</kbd>

```
![狗](./dog.jpg)
```

### 文内跳转链接

方法：<kbd>[Text]</kbd>+<kbd>(#标题)</kbd>

```
[跳转到加粗](#加粗)
```

[跳转到加粗](#加粗)

## 代码

### 行内代码

方法：<kbd>\`</kbd>+变量+<kbd>`</kbd>

```
`python`中关键字有`def`
```

`python`中关键字有`def`

### 代码块

方法：<kbd>\```+相关语言</kbd>+代码+<kbd>```</kbd>

````
```python
print(a)
```
````

```python
print(a)
```

## 引用

方法：<kbd>></kbd>+Text

```
>2024.10.28
>王特起
```

## 数学公式

### 行内公式

方法：<kbd>\$</kbd>+公式+<kbd>$</kbd>

```
这里求$ a^2+b_2 $的值
```

这里求$ a^2+b_2 $的值​

### 行间公式

方法：<kbd>\$\$</kbd>+公式+<kbd>\$$</kbd>

```
方程组为：
$$
\begin{equation}
  \begin{cases}
   f(x)=1+x+x^2
   \\
   g(x)=a_nx^n+a_{n-1}x^{n-1}+...+a_1x^1
  \end{cases}
\end{equation}
$$
```

方程组为：
$$
\begin{equation}
  \begin{cases}
   f(x)=1+x+x^2
   \\
   g(x)=a_nx^n+a_{n-1}x^{n-1}+...+a_1x^1
  \end{cases}
\end{equation}
$$

### 上标和下标

方法：<kbd>\^</kbd>+上标+<kbd>^</kbd>，<kbd>\~</kbd>+下标+<kbd>~</kbd>

```
a^2^
b~3~
```

a^2^

b~3~
