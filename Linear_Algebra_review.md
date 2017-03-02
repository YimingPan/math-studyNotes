# 线性代数重点

## 前言

回顾大一大二时的数学课，我一直有个困惑：明明我上课听得不错，作业也都会自己做，考试分数也很高（基本90分以上），但是到大四的时候却基本忘得差不多，以致于做毕设的时候看论文，被数学折磨得死去活来。后来发现，有我这种困惑的人还不少。直到最近听了麻省理工学院的线性代数公开课，我才恍然大悟。我们的数学课太“学术”，并且偏重习题，学生学完之后留下的印象更多是数学概念和解题方法，缺少如同1+1=2一样自然的常识性认识。当然，有些年轻老师只会念ppt，这种情况就不谈了。因此，我们学的数学知识注定很难记住，除了个别十分聪明的人能悟到其中的奥妙，对于大多数人而言，都是考完便忘。

本人虽才疏学浅，却有造福天下的善心，于是决定写下这篇东西。这篇东西并不是考试复习提纲。我希望写下一些能让你把握住线性代数核心的东西，能让你明白，线性代数到底研究了什么，有什么用。

麻省理工学院的线性代数公开课主页在[这里](https://ocw.mit.edu/courses/mathematics/18-06sc-linear-algebra-fall-2011/index.htm)，视频源有Youtube和iTunes两个。有iPhone或者iPad的同学还可以上iTunes U搜索MIT的Linear Algebra课程，免费下载视频观看。本文的图片都引自公开课的公共讲义。

本文还在施工中，欢迎提出宝贵建议。可以通过邮件联系我，或者直接在我的GitHub项目主页上发issue（如果你会用GitHub的话）。

我的邮箱：yimingp@andrew.cmu.edu
我的GitHub项目主页：https://github.com/YimingPan/math-studyNotes

目前只写到3.2之前

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

![row-picture](img\row-picture.jpg)

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

![column-picture](img\column-picture.jpg)

请特别留意一下这种理解方法，这在后面很有用。

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

从列视角来看，矩阵A和向量b作乘法相当于把A的各列进行组合，用线代的“行话”来说叫“线性组合”。现在我们再观察一下下面这个式子：
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

$$
\left[ \begin{matrix}
1\\
3
\end{matrix} \right]
\left[ \begin{matrix}
1 & -1
\end{matrix} \right]
=
\left[ \begin{matrix}
1 & -1\\
3 & -3
\end{matrix} \right],
\left[ \begin{matrix}
2\\
4
\end{matrix} \right]
\left[ \begin{matrix}
1 & 1
\end{matrix} \right]
\left[ \begin{matrix}
2 & 2\\
4 & 4
\end{matrix} \right]
$$

这次我的用意可能不太明显。你把这两个矩阵加起来试试？是不是又得到了原来那个矩阵乘法的解？这个例子产生的结论是：**A的每一列和B的每一行相乘，得到的一系列矩阵加起来，等于AB**。

矩阵乘法除了定义之外的三种理解方式在实际学习中更加有用，它能帮你更好地理解一些东西。

### 3. 初等变换与矩阵消元

#### 3.1 初等变换

初等变换分为行初等变换和列初等变换，概念很简单，就不再复述了。比较重要的是，初等变换可以用矩阵乘法来表示。行初等变换可以描述为$E_p...E_2E_1A$，列初等变换可以描述为$AE_1E_2...E_q$。行初等变换矩阵乘在左边，列初等变换乘在右边。

**排列矩阵**
排列矩阵是一种特殊的初等变换矩阵，它的作用是交换原矩阵的某些行或某些列，相当于对其进行重新排列，所以叫排列矩阵。一个典型的$3 \times 3$排列矩阵如下：

$$
\left[ \begin{matrix}
1 & 0 & 0\\
0 & 0 & 1\\
0 & 1 & 0
\end{matrix} \right]
$$

排列矩阵可以由单位矩阵交换某些行或某些列得到，所以它每行每列必定只有一个1，剩下全是0。

#### 3.2 高斯-约当消元

别误会，这就是教材里讲的消元法，只是这个名字书里未必会写，我觉得它很酷炫，所以特地标明。

### 4. Ax=b的解法及其几何意义

### 5. 四大子空间

### 6. 秩，线性相关性

## 第二部分：行列式，特征值与特征向量

### 1. 行列式的意义

我大一学线代的时候，教材里对行列式的定义十分恶心，而且不讲行列式的来由，直接空降概念，导致我一直不知道为什么要搞出个这个破玩意儿。但行列式又确实是个重要的东西，所以有必要深入理解它的本质。



