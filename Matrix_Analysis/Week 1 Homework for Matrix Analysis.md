#MA 

##### 1120212364 ，孙宇皓

## Problem 1
假设线性空间 $V$ 的子空间 $W_1$ 是由一组基 $\alpha_1,\alpha_2,\cdots,\alpha_n$ 张成的，那么，线性空间 $V$ 必然是由更多的基张成的。不失一般性，我们取张成 $V$ 的基为 $\alpha_1,\alpha_2,\cdots,\alpha_n\ ,\ \beta_1,\beta_2,\cdots,\beta_m$
那么我们将 $W_2$ 构造为由基 $\beta_1,\beta_2,\cdots,\beta_m$ 张成的空间，从而 $V = W_1+W_2$。
此时，$\mathrm{dim}(W_1)=n$，$\mathrm{dim}(W_2) = m$，$dim (V) = m+n$，利用子空间的维度公式：
$$
\mathrm{dim}(W_1 \cap W_2)+\mathrm{dim}(W_1+W_2) = \mathrm{dim}(W_1)+\mathrm{dim}(W_2)
$$
可知 $\mathrm{dim}(W_1+W_2) = 0$，这意味着 $W_1$ 与 $W_2$ 两个子空间的交中只有零向量，从而，$V=W_1+W_2$ 是 $W_1$ 和 $W_2$ 两个子空间的直和。

## Problem 2
因为 $A$ 是实对称矩阵，所以设 $A$ 合同到一个矩阵 $\Lambda$，有 $A = P^T\Lambda P$ 成立，$P$ 是正交矩阵，$\Lambda$ 的对角元是 $A$ 的本征值。
从而，
$$
x^TAx = x^TP^T\Lambda Px = (Px)^T\Lambda (Px)
$$
$P$ 矩阵代表正交变换，而正交变换是保长度的，因此 $(Px)^T (Px) = 1$，下面证明这一点
$$
(Px)^T(Px) = x^TP^TPx = x^TIx = x^Tx = 1
$$
记 $y=Px, y = [y_1, y_2,\cdots,y_n]^T$，那么 $y^Ty=1$
$$
x^TAx = y^T\Lambda y=\sum_{i=1}^n \lambda_iy_i^2
$$
在 $\sum_i y_i^2=1$ 的约束条件下，显然，若 $\lambda_i$ 是最大特征值，$y_i=1, y_{j\not =i}=0$ 时，$x^TAx$ 取到最大值。因此，$\max x^TAx$ 是 $A$ 的最大特征值，而 $\min x^TAx$ 是 $A$ 的最小特征值。

