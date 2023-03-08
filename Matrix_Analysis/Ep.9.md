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