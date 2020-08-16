# nn

## 问题背景

少年爱迪生梦里无师自通矩阵以后，突然想到矩阵连乘加激活非常像有智能的样子，于是他开始做起了实验。但是当他把矩阵准备好以后，却发现自己不会读他们了，于是他找到了你。

## 问题描述

在本题目中，你需要通过修改`nn.py`完成以下功能

1. 打开输入HDF5文件（路径为 sys.argv[1]），并将其中的 "/nn" 组的三个数据集"fc1","fc2"以及"vec"取出，并将其储存为numpy数组。
我们保证"fc1"是个(m,n)形状的矩阵，保证"fc2"是个(p,m)形状的矩阵，保证"vec"是个(n)形状的向量。
2. 对取出的numpy数组做下列运算（伪代码）
    ```
    imm = fc1 * vec
    act = ReLU(imm)
    res = fc2 * act
    argmax = argmax(res)
    ```
需要注意的是，`*`为矩阵乘法（普通的`*`可能可以运行，但结果可能不是预期结果）。ReLU函数是指，对于输出向量的每个元素，如果大于等于0，则保留原数值，如果小于0，则该元素变为0。argmax函数是指，取出最大元素对应的下标（我们约定下标从0开始，与程序中表示相同）。
3. 将argmax作为数据集"argmax"保存到输出HDF5文件中（路径为 sys.argv[2]）


## 环境配置、样例与评分
