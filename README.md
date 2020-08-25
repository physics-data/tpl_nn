# nn

## 问题背景

少年爱迪生梦里无师自通矩阵以后，突然想到矩阵连乘加激活非常像有智能的样子，于是他开始做起了实验。但是当他把矩阵准备好以后，却发现自己不会读他们了，于是他找到了你。

## 问题描述

在本题目中，你需要通过修改 `nn.py` 完成以下功能

1. 打开输入HDF5文件（路径为 `sys.argv[1]`），并将其中的 "/nn" 组的三个数据集 "fc1", "fc2" 以及 "vec" 取出，并将其储存为 numpy 数组。
我们保证 "fc1" 是个 (m,n) 形状的矩阵，"fc2" 是个 (p,m) 形状的矩阵，"vec" 是个 (n) 形状的向量。
2. 对取出的numpy数组做下列运算（伪代码）
    ```
    imm = fc1 * vec
    act = ReLU(imm)
    res = fc2 * act
    argmax = argmax(res)
    ```
    需要注意的是，`*` 为矩阵乘法（普通的 `*` 可能可以运行，但结果可能不是预期结果）。ReLU 函数是指，对于输出向量的每个元素，如果大于等于 0，则保留原数值，如果小于 0，则该元素变为 0。argmax 函数是指，取出最大元素对应的下标（我们约定下标从 0 开始，与程序中表示相同）。如果代码执行正确，`imm` 和 `act` 应当是 (m) 形状的向量，`res` 是 (p) 形状的向量，最后的结果是标量。
3. 将 argmax 作为数据集 "argmax" 保存到输出HDF5文件中（路径为 `sys.argv[2]`）
4. 将 "/y" 读出储存为向量，使用均方误差作为损失函数，计算argmax 与 y 之间的误差，利用反向传播算法，计算得到 fc1 中，作出变化绝对值最大元素的两个下标值（x 和 y），并将其作为一维数组储存在输出的 "fc1_max_pos" 数据集中

（对于反向传播算法，由于实在不好写公式，请参见 readme.pdf）

## 环境配置、样例与评分

对于每个测试例子，"argmax"占一半的分数，"fc1_max_pos"占另一半的分数。

我们在 `data` 目录下提供了八组数据，分别对应不同的情况和数据量大小。和之前的题目一样，你可以通过 `python3 grade.py` 来进行一次的本地测评。

这次会考验你代码编写的效率，如果代码运行的不够快，可能不到黑盒的满分。本题设置了 1s 的时间限制，如果超过了这个时间，评测程序会提示你超时；对于未超时的数据，它会输出你的代码的实际用时。

最终评分以在助教机器上运行的时间为准。所用电脑的 CPU 为 Intel Core i7-8750H。

最终分数构成为：

* 黑盒 80 分：共 8 个测例，每个 10 分
* 白盒 20 分：代码风格（评测不参考pylint，推荐大家自用pylint），Git 使用 20 分（包括恰当注释（一句话一个注释者，倒扣）、合理命名、提交日志等）

助教以 deadline 前 GitHub 上最后一次提交为准进行评测。
