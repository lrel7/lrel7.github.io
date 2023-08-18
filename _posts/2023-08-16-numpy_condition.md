---
title: NumPy使用技巧1：条件运算
tags: NumPy machine-learning
---

在NumPy中，条件运算允许你根据条件对数组的元素进行逐个操作，无需显式地编写循环

### 创建布尔数组
将条件应用于数组，从而创建一个布尔数组，其中的元素表示原数组每个位置是否满足条件
```python
import numpy as np
arr = np.array([1, 2, 3, 4, 5])
condition = arr > 3 # 创建布尔数组
print(condition)
```
输出结果为：
```shell
[False False False True True]
```

---
### 使用布尔数组索引
可用于选出原数组中满足条件的元素
```python
selection = arr[condition] # 选择满足条件的元素
print(selection)
```
输出结果为：
```shell
[4 5]
```

---
### 条件运算
使用布尔数组，将原数组中满足条件的元素置为特定值
```python
arr[condition] = 0 # 将大于3的元素置为0
print(arr)
```
输出结果为：
```shell
[1 2 3 0 0]
```

---
### 逻辑运算
可以使用逻辑运算符`&`（与），`|`（或），`~`（非）来组合多个布尔数组的条件
```python
condition_combined = (arr > 1) & (arr < 4)
selection_combined = arr[condition_combined]
```
输出结果为：
```shell
[2 3]
```
