# 线性代数总结

## 第一部分：Ax=b，四大子空间

### 1. 线性方程的三种视图

线性代数的研究起点是解线性方程组。看以下方程组：

$$
\begin{aligned}
2x-y & =0 \\
-x+2y & =3
\end{aligned}
$$

我们可以通过三种视角来看待它。
**行视角（Row Picture）**
这是学习线性代数之前我们认识线性方程组的方式：把它看做平面上几条直线求交点，每个方程对应一条直线。
==（补一张图）==

**列视角（Column Picture）**
这是从向量的角度看待线性方程组。上面的线性方程组可以改写成向量形式:

$$
\left[ \begin{matrix}
2\\
-1
\end{matrix} \right]
x+
\left[ \begin{matrix}
-1\\
2
\end{matrix} \right]
y=
\left[ \begin{matrix}
0\\
3
\end{matrix} \right]
$$

==补一张图==

**矩阵视角（Matrix Picture）**
就是我们最熟悉的$Ax=b$形式:

$$
\left[ \begin{matrix}
2 & -1\\
-1 & 2
\end{matrix} \right]
\left[ \begin{matrix}
x\\
y
\end{matrix} \right]
=
\left[ \begin{matrix}
0\\
3
\end{matrix} \right]
$$

### 2. 矩阵乘法的意义

关于矩阵乘法的规则书上都有定义，没有赘述的必要。这里想说一点很有启发性的东西。

我们看几个简单的例子，来获取一些直观的感受。
例2.1：

$$
\left[ \begin{matrix}
1 & 2\\
3 & 4
\end{matrix} \right]
\left[ \begin{matrix}
1\\
1
\end{matrix} \right]
=
\left[ \begin{matrix}
3\\
7
\end{matrix} \right],
\left[ \begin{matrix}
1 & 2\\
3 & 4
\end{matrix} \right]
\left[ \begin{matrix}
-1\\
1
\end{matrix} \right]
=
\left[ \begin{matrix}
1\\
1
\end{matrix} \right]
$$

从列视角来看，矩阵A和向量b作乘法相当于把A的各列进行组合，用线代的“行话”来说叫“线性组合”，在第六节”秩，线性相关性“中会介绍。现在我们再观察一下下面这个式子：
例2.2

$$
\left[ \begin{matrix}
1 & 2\\
3 & 4
\end{matrix} \right]
\left[ \begin{matrix}
1 & -1\\
1 & 1
\end{matrix} \right]
=
\left[ \begin{matrix}
3 & 1\\
7 & 1
\end{matrix} \right]
$$

这一次我做了一个矩阵乘法。你可能已经注意到了，结果矩阵的列恰好是刚刚得到的两个结果向量拼在一起的。这是巧合吗？

显然，这并不是巧合。**如果有两个矩阵AB相乘，A在左B在右，那么B的第j列将决定结果矩阵的第j列，其他列都和它没关系。**

我们换个角度再看待一下例2.1。
例2.3

$$
\left[ \begin{matrix}
1 & 2
\end{matrix} \right]
\left[ \begin{matrix}
1 & -1\\
1 & 1
\end{matrix} \right]
=
\left[ \begin{matrix}
3 & 1
\end{matrix} \right],
\left[ \begin{matrix}
3 & 4
\end{matrix} \right]
\left[ \begin{matrix}
1 & -1\\
1 & 1
\end{matrix} \right]
=
\left[ \begin{matrix}
7 & 1
\end{matrix} \right]
$$

我猜你应该已经明白我的用意了。没错！我们还可以从行的角度理解矩阵之间的乘法：**如果有两个矩阵AB相乘，A在左B在右，那么A的第i行将决定结果矩阵的第i行，其他行都和它没关系！**

游戏还没结束，还有例2.4：

### 3. 高斯-约当消元

### 4. Ax=b的解法及其几何意义

### 5. 四大子空间

### 6. 秩，线性相关性

## 第二部分：行列式，特征值与特征向量

### 1. 行列式的意义

我大一学线代的时候，教材里对行列式的定义十分恶心，而且不讲行列式的来由，直接空降概念，导致我一直不知道为什么要搞出个这个破玩意儿。但行列式又确实是个重要的东西，所以有必要深入理解它的本质。



