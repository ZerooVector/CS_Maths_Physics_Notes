#MA
# 向量组及向量组拼成的抽象矩阵
设 $V$ 是 $F$ 上的线性空间，则 $V$ 中有限个元素 $\alpha_1,\cdots ,\alpha_n$ 构成的序列称为 $V$ 中的一个向量组。
如果将向量组有序地排成一行，则 $[\alpha_1,\alpha_2,\cdots,\alpha_n]$ 则称为向量组拼成的抽象矩阵
当然，你也可以将每个向量作为行向量，拼成一个 $[\alpha_1,\alpha_2,\cdots ,\alpha_p]$ 的矩阵

## 线性相关性
我们从几何空间转入了抽象程度更高的线性空间，现在，我们试图研究线性空间中的“坐标架”——也就是基向量。
向量组 $\alpha_1\cdots \alpha_p$ 中，如果可以找到 $p$ 个非零的数，使得
$$
\sum_i\alpha_ik_i = 0 \qquad (\star)
$$
则称它们线性相关
而如果 $\forall[k_1, k_2,\cdots , k_p]^T \not =0, 0 \in \mathbb F^n$，都不能使得 $\star$ 式成立，则这一个向量组线性无关。
或者说，如果希望 $\star$ 成立，则必须使得 $\alpha_i=0$，则称这些向量线性无关。

**注：线性相关性的矩阵表述**
这种线性组合可以写成方程组的形式：
$$
[\alpha_1,\alpha_2,\cdots ,\alpha_n][x_1,x_2,\cdots,x_n]^T = 0
$$

线性相关->方程组有非零解；线性无关 ->只有零解

## 两个向量组之间的线性表示
现在找到两个向量组 $\alpha_1,\cdots,\alpha_p$ 和 $\beta_1,\cdots,\beta_q$，我们称 **向量** $\beta_i$ 可以被**向量组** $\alpha$ 线性表示，则 $\beta_i$ 可以写成 $\alpha$ 中各个向量的线性组合。
如果**向量组**$\beta$ 可以被**向量组**$\alpha$ 线性表示，则 $\beta$ 中的每一个向量都可以被 $\alpha$ 线性表示。

**注：矩阵表述**
$\beta_i$ 可以被 $\alpha$ 线性表示，可以描述为：
$$
[\alpha_1,\alpha_2,\cdots ,\alpha_n][x_1,x_2,\cdots,x_n]^T = \beta_i
$$
有解！（不一定是非零解！）
$\beta$ 可以被 $\alpha$ 线性表示，则
$$
[\alpha_1,\cdots ,\alpha_n] X = [\beta_1,\cdots,\beta_n]
$$
$X$ 是一个矩阵，第一列是组合出 $\beta_1$ 的系数，以此类推
此矩阵方程有解！

线性表示的关系有传递性。设有向量组 $\alpha_1,\cdots,\alpha_p;\beta_1,\cdots,\beta_q;\gamma_1,\cdots,\gamma_t$，如果 $\beta$ 可由 $\alpha$ 线性表示，$\gamma$ 可由 $\beta$ 线性表示，则 $\gamma$ 可以被 $\alpha$ 线性表示。
##### PF:
首先，$B$ 可以有 $A$ 线性表示，说明方程组
$$
AX = B
$$
有解。同理
$$
BY=C
$$
有解。那么
$$
C= BY = A(XY) = AZ
$$
因此，$C$ 可以由 $A$ 线性表出。
这展示了方程组语言和矩阵运算的强大威力，我们不需要再用自然语言详细地说明了。

## 向量组的极大线性无关组
$\beta_1\cdots \beta_s$ 称为 $\alpha_1\cdots \alpha_p$ 的一个子组（子序列）

