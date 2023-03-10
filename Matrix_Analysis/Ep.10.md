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
利用不变因子的分解，我们可以使得矩阵中的每一块都分到一个不变因子









