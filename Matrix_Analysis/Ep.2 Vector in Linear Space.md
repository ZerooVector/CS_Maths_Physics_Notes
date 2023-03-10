---
banner: "![[banner7.png]]"
---
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

## 向量组的极大线性无关子组
$\beta_1\cdots \beta_s$ 称为 $\alpha_1\cdots \alpha_p$ 的一个子组（子序列）. $\beta$ 是 $\alpha$ 的极大线性无关子组，则：
- $\beta$ 内的各个向量线性无关
- 取 $\alpha$ 的子组 $\gamma_1,\gamma_t$, $t=p+1$，$\gamma$ 中的向量线性相关
也可以换个说法：
$\forall \alpha_i \in \alpha$，$\alpha_i$ 可由 $\beta$ 线性表出（生成性）
##### PF: 留做习题答案略，读者自证不难（这里怀疑有问题，应该是唯一地线性表出）
---

有一个向量组 $\alpha_1,\alpha_2,\cdots,\alpha_n$，从中抽取若干向量组成向量组 $\beta_1,\beta_2,\cdots ,\beta_m$。若 $\forall \alpha_i \in \alpha$，均可由向量组 $\beta$ 线性表出，且表示方式唯一，问：$\beta$ 是 $\alpha$ 的极大线性无关组吗？是，则给出证明，不是，则说明理由（举出反例）。
**笔者的证明**：
首先，我们说明 $\beta$ 中的各个向量是线性无关的。假如 $\beta$ 中的向量线性相关，则其中的任意一个向量 $\beta_k$ 必然可以由其他向量线性表出，也就是
$$
\beta_k = \sum_{i\not = k} w_i\beta_i \qquad (\star)
$$
那么，假设向量组 $\alpha$ 中的某一个向量在被线性表示时，使用了 $\beta_k$，也就是：
$$
\alpha_t = \omega_1\beta_1+\cdots +\omega_k\beta_k+\cdots +\omega_m\beta_m \qquad (\star\star)
$$
那么它必然也存在不用 $\beta_k$ 的表示方式，也就是将 $\star$ 式代入 $\star\star$ 式。这与题设矛盾。因此，$\beta$ 中的各个向量必须是线性无关的。
再来说明 $\beta$ 是极大的。因为 $\alpha$ 中的任意向量都可以由 $\beta$ 线性表出，因此，如果再从 $\alpha$ 中取一个向量加入 $\beta$，必然使得 $\beta$ 中各个向量线性相关，这与前文的推导矛盾。因此 $\beta$ 是极大的。
综上，$\beta$ 是 $\alpha$ 的极大线性无关组。

---
那么，母组可以由其极大线性无关子组线性表示。

现在，我们希望探究极大线性无关子组中向量的个数。
##### Theorem 
向量组的极大线性无关组所含的向量的个数是唯一的。

##### PF
设 $\alpha$ 的两个极大组为 $\beta_1,\cdots,\beta_s$；$\gamma_1,\cdots,\gamma_t$。假设 $s\not = t$，不失一般性，设 $s<t$，将 $\alpha$ 作为；列向量，组成的矩阵记为 $A$，$\beta$ 组成的记为 $B$，$\gamma$ 组成的记为 $C$。由于 $A$ 可以由 $B$ 生成，因此
$$
BX = A
$$
有解。而 $C$ 显然可由 $A$ 线性表出，那么
$$
AY = C
$$
以上两式联立，得：
$$
BZ =BXY= C \qquad(\star)
$$
有解。这说明，利用 $B$ 可以线性表示 $C$
$C$ 是 $1\times t$，$B$ 是 $1\times s$，因此 $Z$ 是 $s\times t$，由于假定了 $s<t$，那么
##### 引理
行数小于列数的线性方程组必有非零解。这是因为方程的数量小于未知数的数量（不定方程）
要证引理，可以用数学归纳。先从一行的情况开始。之后，多于 1 行的方程组可以使用 Gauss 消元消到只剩一行；$k+1$ 行的方程组总可以消到 $k$ 行。由此引理可证。
于是，将原方程组中的 $Z$ 作为系数矩阵，构成一个新的方程组
$$
ZW=0
$$
必然有非零解。
在 $\star$ 两端同时乘 $W$，那么我们有：
$$
B(ZW) = CW = 0
$$
这与 $C$ 是极大线性无关子组的事实矛盾。

总之，这里使用了极大线性无关子组的矩阵表示，以及利用了它可以“生成”整个向量组的特性。这说明，一个向量组的极大线性无关子组中向量的个数是不依赖于挑选方式的，这称为极大线性无关子组的秩 (Rank)。

由于这样的特性，我们就可以从一个向量组里面选出几个代表性的向量，作为“坐标架”

## 基和坐标
$V$ 是 $\mathbb F$ 上的线性空间，若有正整数 $n$，及 $V$ 中向量组 $\alpha_1,\cdots,\alpha_n$ 使得
- 线性无关性：$\alpha$ 中各个向量线性无关
- 生成性： $\forall \alpha \in B,\alpha = \sum_i\alpha_ik_i$
- 或者 $\alpha = [\alpha_1,\cdots,\alpha_n][k_1,k_2,\cdots,k_n]^T$
则称 $\alpha$ 是 $n$ 维线性空间上的一个基，也称为坐标系。$[k_1, k_2\cdots,k_n]$ 则称为 $\alpha \in V$ 沿着该坐标系的坐标向量。
也就是说，一个抽象向量等于基矩阵乘以坐标向量。







