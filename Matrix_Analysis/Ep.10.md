#MA 

在上一节中，我们看到了将一个数域上矩阵的相似转化为特征矩阵的等价，且特征矩阵只有 $p$ 个非 1 的不变因子。下面，我们将对 $h_i(\lambda)$ 进行质因式分解，从而将特征矩阵的 Smith 标准型化简为一个更加特殊的形式。

##### Def 特征矩阵的初等因子组
将不变因子 $h_i(\lambda)$ 在 $\mathbb{F}(\lambda )$ 内进行质因式分解出现的质因子的方幂，每一个叫做一个初等因子，所有的初等因子的集合叫做初等因子组。注意：一个初等因子可能出现多次，不需要把重复的扔掉。

##### Example 初等因子组与不变因子互相唯一决定
下证，不变因子由初等因子组唯一决定.
例如，有 $A \in \mathbb{C}^{8\times8}$ ，已知其初等因子组为 $\lambda,\lambda^2,\lambda,(\lambda+1)^2,(\lambda+1)^2$，那么我们可以还原出不变因子（依据不变因子的整除规律）：
显然，$d_{8}(\lambda) = \lambda^{2} (\lambda+1)^{2}, d_{7}(\lambda)= \lambda (\lambda+1)^{2}, d_{6}(\lambda) = \lambda$，剩下的全是 1.

##### Theorem 总结：矩阵相似的各种描述
对于 $\mathbb{F}^{n\times n}$ 中矩阵 $A$ 和 $B$ ，以下等价：
- $A$ 与 $B$ 相似
- $\lambda I-A$ 与 $\lambda I-B$ 等价
- $\lambda  I -A$ 与 $\lambda I-B$ 的 Smith 标准型相同
- $\lambda I-A$ 与 $\lambda I-B$ 有相同的不变因子
- $\lambda I-A$ 与 $\lambda I-B$ 有相同的行列式因子
- $\lambda I-A$ 与 $\lambda I-B$ 有相同的初等因子组

##### Example 例题：证明 $A^T$ 和 $A$ 相似
显然，最优的做法是利用行列式因子。$\lambda I - A$ 与 $(\lambda I -A)^{T}$ 有相同的行列式，它们也必然有相同的行列式因子。

## Jordan 标准型
考虑 $\mathbb{F} = \mathbb{C}$，那么这里的多项式都可以分解。
记一个特征矩阵的不变因子可以分解为：
$$
h_{i}(\lambda) = (\lambda-c_{1})^{r_{1}}(\lambda-c_{2})^{r_{2}} \cdots 
$$
##### Lemma 
$$
\mathrm{diag}(1,1,\cdots,h_i(\lambda)) \sim \rm{diag}(1,1,\cdots ,(\lambda-c_{1})^{r_{1}};1,1,\cdots ,(\lambda-c_{2})^{r_{2}};\cdots )
$$
利用不变因子的分解，我们可以使得矩阵中的每一块都分到一个初等因子。于是，
$$
\lambda I - A \sim \mathrm{diag}(J_{1}(\lambda),J_{2}(\lambda),\cdots ,J_{n}(\lambda))
$$

那么，现在有许多的 $A$，对应的 $J(\lambda)$ 都是相同的。现在，我们已知 $J(\lambda)$，希望找出一个尽可能简单的矩阵 $J$，使得 $\lambda I - J$ 仍然可以化成 $J(\lambda)$ 的形式。那么，我们找出的矩阵 $J$ 就是 Jordan 标准型。
==这里需要一个证明==


我们可以给每一小块找到一个对应的 $J$ 矩阵，
使得
$$
\lambda I_{r_{i}} - \begin{bmatrix}c_{1} & 1 & 0 & \cdots & 0  \\ 0  & c_{2} & 1 & \cdots & 0 \\ \cdots \end{bmatrix}   \sim J_{i}(\lambda)
$$
那么，要说明两个多项式矩阵等价，我们有三个方法：
- 方法 1：由等价的定义，进行初等变换
- 方法 2：计算两侧的行列式因子
对于左边，我们可以挑选出一个 $n-1$ 阶的矩阵，使得其是一个下三角矩阵，其行列式等于所有对角元相乘，因此，其 $r_{i}-1$ 阶行列式中有一个是 1，那么 $r_{i}-1$ 阶行列式因子只能是 1. 而右侧的 $r_{i}-1$ 阶行列式因子显然是 1.

##### Def Jordan 标准型
$A\in \mathbb{C}^{n\times n}$，$\lambda  I-A$ 的初等因子组为：$(\lambda-c_{1})^{r_{1}},\cdots,(\lambda-c_{q})^{r_{i}}$，取
$$
J_{i}= \begin{bmatrix}c_{1} & 1 && \\ &c_{2}&1 & \\ \cdots\end{bmatrix}
$$
一直排列下去，再取
$$
J = \mathrm{diag}[J_{1},J_{2},\cdots]
$$
则 $J$ 称为 $A$ 的 Jordan 标准型，显然，$A\sim J$

##### Def 复数域上矩阵的特征结构
按照相似的定义：
$$
P^{-1}AP = J
$$
或者我们写成：
$$
AP =PJ
$$
其中，$J$ 是对角块，我们将 $P$ 分块：$P = [P_{1},P_{2},\cdots ,P_{q}]$，那么：
$$
A[P_{1},P_{2},\cdots ,P_{q}] = [P_{1},P_{2},\cdots,P_{q}]\mathrm{diag}(J_{1},J_{2},\cdots ,J_{q})
$$
任取其中一块：
$$
AP_{i}= P_{i}J_{i}
$$
也就是说，$\mathrm{im} P_{i}$ 构成的子空间，是 $A$ 的不变子空间，而且，所有 $P_i$ 的列向量组构成全空间的一组基。
从控制理论上来说，这是一种 decouple 的操作，将 $AP=PJ$ 这个大的方程组变成了 $AP_{i} = P_{i}J_{i}$ 这样的一系列小方程，也就是说，系统的“一组”输入量仅影响“一组”输出量

如果我们从细节上再来观察一下：
$$
\begin{align*}
Ap_{1}&= p_1c_1\\
Ap_{2}&= p_1+p_2c_2\\
Ap_{r} &= p_{r-1}+p_{r}c
\end{align*}
$$













