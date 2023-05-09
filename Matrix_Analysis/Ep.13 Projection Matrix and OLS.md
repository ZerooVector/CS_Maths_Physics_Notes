#MA 

## 最佳逼近问题-续

##### Theorem 有限维投影定理
设 $V$ 是 $\mathbb{C}$ 的内积空间，$\beta \in V$，$W$ 是 $V$ 的有限维子空间，则存在唯一 $\alpha\in W$，使得
$$
\mathrm{d}(\alpha,\beta) \le \mathrm{d}(w,\beta)
$$
也就是说：
$$
\alpha = \arg \min_{w \in W} d(w,\beta)
$$
我们设 $\beta_{1},\beta_{2},\cdots ,\beta_{k}$ 是 $W$ 的一组基，那么：
$$
\alpha  = \beta_{1}k_{1}+\cdots +\beta_{s}k_{s} = [\beta_{1},\beta_{2},\cdots,\beta_{k}]k
$$
那么，：
$$
k = G(\{\beta_{i}\})^{-1} G(\{\beta_{i}\},\beta )
$$
其中，$G(\{\beta_{i}\})$ 是 $\{\beta\}$ 的 Gram 矩阵，$G(\{\beta_{i}\},\beta )$ 是 $\{\beta_{i}\}$ 与 $\beta$ 的 Co-Gram 矩阵

##### PF
首先，我们来说明 $\alpha$ 是 $\beta$ 在 $W$ 中的投影时，$\alpha$ 和 $\beta$ 是最接近的。
那么，此时，$(\beta-\alpha) \bot W$，也就是说，$(\beta-\alpha)$ 垂直于 $W$ 中的任意一个向量。在 $W$ 中任取一个向量 $w$，那么，$d (\beta, w) = ||\beta-w||$ 
此时，$(\beta -\alpha) \bot (\alpha-w)$ ，根据勾股定理，
$$
||\beta-w||^{2} = ||\beta-\alpha||^{2}+||\alpha-w||^{2}
$$
显然，$||\beta -w||^{2}\ge ||\beta-\alpha||^{2}$ ，也就是说，点到平面所引的所有线段中，直线最短。

下面，我们说明使得距离取到最小值的 $\alpha$ 必定存在：
如果 $(\beta-\alpha) \bot W$，那么 $(\beta-\alpha)\bot \beta_{j}$ ，也就是说：
$$
\langle  \beta_{j},\beta-\alpha \rangle = 0
$$
利用内积的线性性将上式展开，有：
$$
\langle  \beta ,\sum_{i}\beta _{i}k_{i} \rangle = \langle  \beta_{j},\beta \rangle
$$
再次展开，有：
$$
\sum_{i} \langle  \beta_{j},\beta_{i}  \rangle k_{i} = \langle  \beta_{j},\beta  \rangle \quad \forall \beta_{j} 
$$
将其写成方程组的形式，容易看出上面的结论。

最后，我们来证明唯一性。若存在 $\tilde \alpha\in W,\tilde \alpha \not = \alpha$，使得 $d (\beta ,\tilde \alpha) = d(\beta,\alpha)$ ，这与勾股定理矛盾。
因此，唯一性也得到了保证。
**这样的推导过程表明，最佳逼近问题的实质是一个多元函数求极值问题** ，实际上，你可以这样做：
$$
\begin{align*}
d(\alpha,\beta)^{2}\\
&= \langle  \beta-\sum_{i}\beta_{i}k_{i},\beta-\sum_{i}\beta_{i}k_{i} \rangle\\
&= ||\beta||^{2}-2\sum_{i} \langle  \beta ,\beta_{i} \rangle+[k_{1},\cdots ,k_{s}]G(\beta_{i})[k_{1},\cdots ,k_{n}]^T 
\end{align*}
$$
通过对各个 $k_{i}$ 偏导，即可得到上面的方程组。但是，这个算法通常仅仅使得一阶偏导取到 0，无法证明充分性。

##### Example 某个向量在一维子空间中的正交投影
考虑将向量 $\beta = [2,1,0,2]$ 向着一维子空间 $W = \mathrm{span}\{\beta_{1}=[0,1,, i,\frac{1}{2}]\}$ 投影，代入公式，你发现：
$$
\alpha=\beta_{1} \frac{\beta_{1}^{H}\beta}{\beta_{1}^{H}\beta_{1}}
$$
容易直接看出，这的确是一个投影

##### Example 
考虑 $A \in \mathbb{C}^{n\times s}$ 列满秩，现在要将 $\beta \in \mathbb{C}^{n}$ 投影到 $\mathrm{im}(A)$ 上，记投影得到的向量为 $P_{A}(\beta)$，那么：
$$
P_{A}(\beta) = Ak=AG(\mathrm{col}(A))^{-1}G(A,\beta) = A(A^{H}A)^{-1}A^H \beta
$$
第一步是说，投影的结果是 $A$ 的各个列向量的线性组合。那么我们发现，对于任意向量左乘
$$
P_{A}= A(A^{H}A)^{-1}A^{H}\beta
$$
就相当于将这个向量投影到了 $A$ 的各列张成的空间中
性质：
- $P_{A}^{H} =P_{A}$
- $P_{A}^{2}=P_{A}$
- $\mathrm{rank}(P_{A}) = \mathrm{rank}(A)$

##### Example 观测数据的最小二乘拟合
最小二乘拟合准则：我们认为这样的拟合是好的：
$$
\min \sum_{i}(f(x_{i})-y_{i})^{2} 
$$
我们只来考虑样本为 $(x_{i},y_{i})$ 这样单变量的 OLS 问题
现在，我们将原问题抽象化：考虑一个子空间 $W$，包含候选多项式的全体，也就是说, $W = \{\sum_{i=1}^{k} a_{i}x^{i}|a \in \mathbb{R}^{k+1}\}$ ，那么，子空间显然有一组基 $[1,x,x^{2},x^{3},\cdots ,x^{k}]$ 。
我们将样本写成列向量的形式：$\beta = [\beta_{1},\cdots ,\beta_{n}]^{T}$ ，基函数在 $n$ 个样本上的采样为：$\beta_{i} = [x_{1}^{i},\cdots ,x_{n}^{i}]$
==这里并没有讲明白==  
$$
\sum |f(x_{i})-y_{i}|^{2} = \sum_{i=1}^{n}|\sum_{j=0}^{k}x_{i}^{j}a_{j}-y_{i}|^{2} = ||(\sum_{j}x_{i}^{j}a_{j}-y_{i})||^{2}
$$
其中，$||(\sum_{j}x_{i}^{j}a_{j}-y_{i})||^{2}$ 是一个向量，每个维度上对应一个 $i$ 
也就是说，我们要最小化以下向量的模：
$$
\begin{bmatrix}x_{1}^{0} \\ \cdots   \\ x_{n}^{0}\end{bmatrix}a_{0}+\begin{bmatrix}x_{1}^{1} \\ \cdots  \\ x_{n}^{1}\end{bmatrix}a_{1}+\cdots  -\begin{bmatrix}y_{1} \\ \cdots   \\ y_{n}\end{bmatrix}
$$
也就是说，最小二乘是将真实的因变量向着 $k+1$ 个基函数在自变量上的采样投影！


