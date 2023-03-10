#MA  

## 数域上矩阵的特征矩阵

##### Theorem 单位模阵可以写成初等矩阵的乘积
- **单位模阵的 Smith 型是单位矩阵**。这可以利用 $|U(\lambda)|=C$ 的结论证明：$U(\lambda)$ 的 $n$ 阶行列式因子为 1，根据不变因子的递推公式，$D_n (\lambda)= \prod d_{i}(\lambda)=1$，那么显然 $d_i(\lambda)=1$ 
-  **单位模阵可以写成初等矩阵的乘积** 。$P_{s}(\lambda),\cdots P_{1}(\lambda) U (\lambda) Q_{1}(\lambda) Q_{2}(\lambda), \cdots Q_{t}(\lambda)=I$
也就是说 $U (\lambda) = P_{s}^{-1}(\lambda)\cdots P_{1}^{-1}(\lambda)I Q_{t}^{-1}(\lambda) \cdots Q_{1}^{-1}(\lambda)$ 由于初等矩阵的逆还是初等矩阵，因此, 结论得证。

##### Def 特征矩阵
给定 $A \in \mathbb{F}^{n\times n}$ ,那么多项式矩阵
$$
\lambda I-A = \begin{bmatrix}\lambda-a_{11} &\cdots & \cdots & -a_{1n} \\ &\cdots&\cdots && \\ -a_{n1}&\cdots &\cdots & \lambda-a_{nn}\end{bmatrix}
$$
称为 $A$ 的特征矩阵

##### Theorem 
数域上的矩阵 $A, B \in \mathbb{F}^{n\times n}$ 相似，意味着它们的特征矩阵等价！也就是说
$$
U(\lambda)(\lambda I-A)V(\lambda) = \lambda I -B
$$
这样的定理为我们研究数域上的矩阵相似提供了方便，因为我们判断矩阵的等价比相似会更简单（可以任意进行初等行列变换）。

而数域上的相似可以表示为：
$$
AP = PB
$$

要想证明这个定理，需要做一些准备
##### Def 多项式矩阵的次数
$$
A(\lambda) = A_{0}+A_{1}\lambda+\cdots + A_{r}\lambda^{r}
$$
若 $A_{r} \not = 0$，则称多项式矩阵是 $r$ 次的，0 多项式矩阵的次数无意义。

##### Lemma 多项式矩阵乘积的次数
考虑 $A (\lambda) \in  \mathbb{F}^{m\times n }[\lambda], B (\lambda), C (\lambda)\in \mathbb{F}^{m\times n }[\lambda]$,其中 $A (\lambda) B (\lambda)= C(\lambda)$ 均非零，且展开 $A(\lambda)$ 时，
$$
A(\lambda) = \sum_{i=0}^{r}A_{i}\lambda^{i}
$$
 $A_{r}$ 可逆，则：$\mathcal{D}(C (\lambda)) = \mathcal{D}(A (\lambda)) + \mathcal{D}(B(\lambda ))$  

##### PF 
$$
\begin{align*}
(A_{0}+A_{1}\lambda+\cdots +A_{r}\lambda)(B_{0}+B_{1}\lambda+\cdots +B_{s}\lambda^{s}) &= (C_{0}+C_{1}\lambda+\cdots + C_{r+s}\lambda^{r+s})
\end{align*}
$$
实际上，这个东西和多项式一样，不可能乘出更高的次数，现在唯一有问题的是：
$$
C_{r+s} = A_{r}B_{s}
$$
这个可能出现问题，乘出 0 矩阵。在 $A_r$ 可逆（满秩）的情况下，$C_{r+s}=0$ 当且仅当 $B_s = 0$

##### Lemma 多项式矩阵的带余除法（左除）
仍然考虑 $$
A(\lambda) = \sum_{i=0}^{r}A_{i}\lambda^{i} \quad \in \mathbb{F}^{m\times m}
$$
再考虑非零的 $B (\lambda)\in \mathbb{F}^{m\times n}[\lambda]$，那么存在唯一的商 $Q(\lambda)$ 和余数 $R(\lambda)$ 使得
$$
B(\lambda) = A(\lambda)Q(\lambda)+R(\lambda)
$$
成立，且 $\mathcal{D}(R (\lambda))<\mathcal{D}(A(\lambda))$ 或者 $R (\lambda) = 0$ 

##### PF
这可以通过小学数学的方式证明（逐步上商的方式）

##### 现在我们返回来证明最初的命题。
如果从相似推向等价，那么只要取 $P^{-1} = U (\lambda), P = V(\lambda)$ 即可
如果我们从多项式矩阵的等价回推相似，那么：
$$
U(\lambda) = (\lambda I-B)Q(\lambda)+R(\lambda) 
$$
那么显然可以注意到，$R(\lambda)$ 要么 0，要么是非 0 的 0 次多项式，总之，$R(\lambda)$ 为常数矩阵，我们将 $R(\lambda)$ 记为 $R$。
我们改写方程，将 $V (\lambda)$ 放到右边
$$
U(\lambda) (\lambda I-A) = (\lambda I -B )V^{-1}(\lambda)
$$
将带余除法代入上式，有：
$$
R(\lambda I -A) = (\lambda I-B)[V^{-1}(\lambda ) - Q(\lambda )(\lambda I-A)]
$$
根据 Lemma 1 ，方程的左侧是常数矩阵，因此，右侧 $[V^{-1}(\lambda ) - Q(\lambda )(\lambda I-A)]$ 也是常数，因此，我们得到：
$$
R(\lambda I - A) = (\lambda I - B)S
$$
通过比较系数可知，$R = S$，现在证 $R$ 可逆，再使用 $U^{-1}$ 进行一次带余除法
$$
U^{-1}(\lambda) = (\lambda I-A)\bar  Q(\lambda) + \bar R 
$$
将 $U^{-1}(\lambda)$ 和 $U(\lambda)$ 的带余除法相乘，那么：
$$
[(\lambda I - B)Q(\lambda)+R][(\lambda I-A)\bar Q(\lambda)+\bar  R ] = I
$$
整理后可得：
$$
R\bar R =  I - (\lambda I -B )[Q(\lambda)U^{-1}(\lambda)+S \bar Q(\lambda)]
$$
这也是一个带余除法式。注意到 $R\bar R$ 是一次的，这比除数的次数还要高，因此，商 0，因此，
$$
R \bar R  =I
$$
成立。
以上命题得证。

## 特征矩阵的标准型
##### Theorem 特征矩阵的 Smith 型
- $\lambda I -A$ 的 Smith 型为 $\mathrm{diag}(d_{1}(\lambda),\cdots ,d_{n}(\lambda))$ ，其中 $\prod d_{i}(\lambda) = |\lambda I -A |$ ，且 $\sum \mathcal{D}(d_{i}(\lambda)) = n$
- $\lambda I-A$ 的多项式一定是 $n$ 次多项式，其秩一定是 $n$ 
设 $d_{i}(\lambda)$ 中有 $p$ 个非常数的不变因子，记为 $h_{1}(\lambda),\cdots ,h_{p}(\lambda)$，其中 $n_{i} = \mathcal{D}(h_{i}(\lambda))$，则不变因子中恰好有 $(n_{1}-1)+(n_{2}-1)+\cdots + (n_{p}-1)$ 个为 1. 一次，它的 Smith 型可以被化成一个更加特殊的情形：$\mathrm{diag}(1,1,1,\cdots,h_{1}(\lambda);1,1,1,\cdots,h_{2}(\lambda);\cdots )$ 就是在每一个多项式的不变因子前面跟上相应数量的 1.




