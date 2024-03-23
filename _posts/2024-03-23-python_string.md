---
title: Python 中的三引号字符串
tags: Python
---

# 简介
在 Python 中，使用三引号 `"""` 或 `'''` 创建的字符串可以包含任意字符，包括单引号、双引号和换行符，而不需要转义。这使得创建包含大量格式化文本的字符串变得更加简单和直观。

# 用法
## 单行文本
文本和引号之间不能有换行：
![](https://lrel7.github.io/assets/images/2024-03-23-python_string/2024-03-23-10-49-48.png)

## 多行文本
直接换行：
![](https://lrel7.github.io/assets/images/2024-03-23-python_string/2024-03-23-10-51-35.png)

## 包含单引号和双引号
![](https://lrel7.github.io/assets/images/2024-03-23-python_string/2024-03-23-10-53-01.png)
![](https://lrel7.github.io/assets/images/2024-03-23-python_string/2024-03-23-10-52-36.png)

## 在代码中换行而不影响字符串
有时候编辑的字符串太长，我们希望换一行来写，但又不希望在字符串中体现，可以使用斜杠 `\` ：
![](https://lrel7.github.io/assets/images/2024-03-23-python_string/2024-03-23-10-56-01.png)