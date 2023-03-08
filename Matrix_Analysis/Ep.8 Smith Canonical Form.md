#MA  

## 复习一下多项式
##### Def 多项式的次数
多项式不为 0 的项的最高次数，称为多项式的次数

##### 带余除法
给出 $f (\lambda)=0$，那么
$$
f(\lambda)= h(\lambda)q(\lambda)+r(\lambda)
$$
余数的次数比除数严格低。

##### 质因式分解
$$
f(\lambda) = \prod_i(q_i(\lambda))^{r_i}
$$
其中，$q_i (\lambda)$ 不可以再被分解因式，因此称为“质因式”
在实数域上的多项式只有两种不可约：（1）一次多项式 $x-c$（2）二次多项式：$x^2+bx+c,\Delta<0$ **注意：三次多项式至少有一个实根**
在复数域上：只有 $x-c$ 这种一次多项式不可约。（**代数基本定理**）

##### 辗转相除法
用于计算最大公约数的辗转相除算法是这样的：
$$
\begin{aligned}
a = bq_1+r_1\\
b = r_1q_2+r_2\\
r_1 = r_2q_3+r_3\\
\cdots\\
r_{k+1} = r_kq_{k+1}
\end{aligned}
$$
总之，给定 $f,g$ 两个多项式，它们的最高公因式可以写作它们的组合：
$$
f(\lambda)h(\lambda)+g(\lambda)t(\lambda)
$$

## Smith 标准型
##### PF 
假如 $A (\lambda)$ 是非零矩阵，那么将 $A$ 中次数最低的变到左上角。再经过一系列降次，就可以得到 $a_{11}(\lambda) \not = 0$，且可以整除**其他所有元素**。那么此时，可以通过初等列变换，将第一列除了 $a_{11}$ 之外全部变成 0，并且将第一行除了 $a_{11}$ 之外全部变成 0.
![[Ep.8 2023-03-03 10.34.40.excalidraw|300]]
但是，还有一个问题是唯一性。因为我们进行初等行列变换的过程中，顺序是不同的。得到的结果是相同的吗？
为了保证结果的唯一性，要求对角线上所有多项式的首项系数全部是 1.

为了研究这种唯一性，我们来引入行列式因子：
##### Def $\lambda$ 矩阵的行列式因子
设 $A (\lambda) \in (F[\lambda])^{m\times n}$，那么 $A (\lambda)$ 的所有一阶子式的最高公因式，称为 $A (\lambda)$ 的 $k$ 阶行列式因子。
记
$$
f(\lambda) = \prod_i^s (q_i(\lambda))^{r_i} \qquad g(\lambda)=\prod_i^t (p_i(\lambda))^{k_i}
$$
我们可以把它们写成相同的质因式的乘积，只不过，当某个质因式不出现时，我们将其系数置为 0：
$$
f(\lambda) = \prod_i^s(q_i(\lambda))^{r_i} \times \prod_i^t(p_i(\lambda))^{k_i}
$$
取出所有系数最低的，就是 $f, g$ 的最高公因式。

##### Theorem  初等变换不改变 $k$ 阶行列式因子
##### Proof
本来的行列式集合为 $\mathcal A$，变换后为 $\mathcal B$
任取 $f (\lambda) \in \mathcal B$，那么所对应的子式可能有三种情况：
- 交换两行，显然成立（每个子式可能只是差符号）
- 某行乘以常数，显然成立（不改变次数，更不可能改变 $k$ 阶行列式因子）
- 现在，只讨论第 $i$ 行乘以 $h (\lambda)$ 加到第 $j$ 行的情况
	- 假如选取的某个子式不含有第 $j$ 行，那么这个子式不变，因此，$f (\lambda) \in \mathcal A$
	- 含有第 $j$ 行，且同时含有第 $i$ 行，那么子式的值不变，因此，$f (\lambda) \in A$
	- 含有第 $j$ 行，但是不含有第 $i$ 行，那么这个矩阵 $[a_1,\cdots,a_j+b_j,a_{j+1},a_n]^T$ ，它的行列式具有分裂性质，$|[a_1,\cdots, a_j+b_j,\cdots, a_n]^T| = |[a_1,\cdots,a_n]^T|+|[a_1,\cdots,b_j,\cdots,a_n]^T|$ ，记作 $f (\lambda) = g (\lambda)+w (\lambda) h (\lambda), g (\lambda) \in \mathcal A, w (\lambda) \in \mathcal A$，也就是说，$f (\lambda)$ 可以写成 $\mathcal A$ 中两个多项式的组合，因此，$\mathcal A$ 的公因式必然可以整除 $f (\lambda)$
- 从而，$\mathcal B$ 中的所有多项式都可以被 $\mathcal A$ 的公因式整除，两个集合的最高公因式必然一致

##### Theorem Smith 标准型的唯一性和不变因子

$$
A(\lambda) = \begin{bmatrix}
\mathrm{diag}(d_i(\lambda)) & O\\
O & O
\end{bmatrix}
$$
满足：
- $\max i = r$，这里的 $r$ 是 $A$ 的秩。
- 记 $k$ 阶行列式因子为 $D_k(\lambda)$，那么 $d_1 (\lambda) = D_1 (\lambda)\ ;\ d_i (\lambda) = D_i (\lambda)/D_{i-1}(\lambda)$ ，这就说明了 Smith 标准型的唯一性（因为任何的初等变换是不改变 $k$ 阶行列式因子的），同时，$d_i(\lambda)$ 称为 $A$ 的不变因子
##### PF 
计算变换前后的各阶行列式因子，即得
例如，在 $k=2$ 的时候，原矩阵的 2 阶行列式因子就是 $D_2 (\lambda)$，标准型：$d_{1}(\lambda) d_{2}(\lambda), d_{1}(\lambda) d_{3}(\lambda),\cdots,d_{r-1}(\lambda)d_{r}(\lambda)$ 的最高公因式，但是，前面的可以整除后面的，所以，它们的最高公因式也就是 $d_{1}(\lambda)d_{2}(\lambda)$ ，显然 $D_2 (\lambda)= d_{1}(\lambda)d_{2}(\lambda)$

##### Example 两种方法求 Smith标准型
求以下矩阵的标准型：
$$
\begin{bmatrix}\lambda(\lambda+1) & 0 & 0  \\ 0 & \lambda& 0  \\ 0 &0& (\lambda+1)^{2}\end{bmatrix}
$$
方法 1：按照初等变换来求解：

方法 2：
$$
D_1(\lambda) = 1
$$
二阶的子式：$\lambda^{2}(\lambda+1),\lambda(\lambda+1)^{3},\lambda(\lambda+1)^{2}$，最高公因式显然是 $\lambda(\lambda+1)$
$$
D_{3} = \lambda^{2}(\lambda+1)^3
$$

