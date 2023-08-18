---
title: NumPy使用技巧2：广播
tags: NumPy machine-learning
---

NumPy的广播（Broadcasting）功能允许你在不同形状的数组之间进行逐元素操作，无需显式地将数组形状调整为相同，提高了代码的可读性与效率

### 广播规则
* 从最右边的维度开始逐一比较，如果两个数组的对应维度大小相同，或其中一个维度大小为1，则认为这两个维度是**兼容**的；否则，这两个数组不能被广播，抛出`ValueError`错误
* 如果数组的维度不同，但有一个数组的维度大小为1，NumPy会自动扩展该数组的形状（方法是复制），使其与另一个数组的形状相匹配

---
### 广播示例
```python
import numpy as np

A = np.array([[1, 2, 3]]) # 1×3的数组
print(1 + A) # 1被复制了3列
```
输出结果为：
```shell
[[2 3 4]]
```

```python
B = np.array([[1, 2, 3], [1, 2, 3]]) # 2×3的数组
print(A + B) # A中的元素被复制了1行
```
输出结果为：
```shell
[[2 4 6] [2 4 6]]
```

```python
C = np.array([[1, 2], [1, 2]]) # 2×2的数组
print(A + C)
```
输出结果为：
```shell
ValueError: operands could not be broadcast together with shapes (1,3) (2,2)
```
