#MLorDS 

***SVM 的基本原理：找到最优的（分类间隔最大）的超平面***

![[Pasted image 20230314171043.png]]
左边两张图可以使用线性的分类方法，右边则只能使用核技巧

## 推导
线性可分是什么意思？从数学上表述，也就是在
$$
\begin{align*}
w^{T}x_{i}+b &\ge 0 \quad y_{i} = +1\\
w^{T}x_{i}+b &\le 0 \quad y_{i} = -1
\end{align*}
$$
其中，$x_{i}$ 是其中一个数据点，$y_{i}$ 是这个数据点的类别。实际上，考虑到我们的问题是线性可分的，我们可以让数据点离开决策边界一定距离，并且，决策边界恰好处在两类数据的中间
$$
\begin{align*}
w^{T}x_{i}+ b \geq 1 \quad y_{i}&= +1\\
w^{T}x_{i}+ b \leq 1 \quad y_{i}&= -1
\end{align*}
$$
上面的两个式子归结起来，就是：
$$
y_{i}(w^{T}x_{i}+b ) \geq 1
$$
考虑到两个超平面间的距离应该是：
$$
\mathrm{dis}(H_{1},H_{2}) = \frac{2}{||w||}
$$
于是，问题转化为一个凸优化问题：
$$
\max \frac{1}{2} ||w||^{2} \qquad s.t.\ y_{i}(w^{T}x+b) \ge 1
$$
## 乘子法，对偶问题
我们难以直接解决这个带有约束的最优化问题，因此我们引入拉格朗日乘子法。我们首先介绍拉格朗日乘子法和最优化中的对偶问题。
假设原始问题为
$$
\begin{align*}
\min f(x)\\
c_{i}(x) &\le 0\\
h_{i}(x)  &= 0 
\end{align*}
$$
那么，这个有约束优化问题的解等于无约束优化问题：
$$
L(x,\alpha,\beta) = f(x) +\sum_{i}\alpha_{i}c_{i}(x) + \sum_{i}\beta_{i}h_{i}(x)
$$
这里，我们可以这样求出原问题的解：先对 $\alpha,\beta$ 求极大（此时问题已经变成了 $x$ 的函数，再对 $x$ 求极小）
$$
\theta_{p}  =  \min_{x} \max_{\alpha,\beta} L(x,\alpha,\beta)
$$
其对偶问题是：
$$
\theta_{d} =  \max_{\alpha,\beta} \min_{x} L(x,\alpha,\beta)
$$
一般来说，我们有：
$$
\theta_{p} \ge \theta_{d}
$$
而在 Slater 条件满足时，等号取到。

## 使用乘子法推导 SVM
使用乘子法将原问题转换成对偶问题：
$$
L(w,b,\alpha) = \frac{1}{2}||w||^{2} +\sum_{i}\alpha_{i}(1-y_{i}(w^{T}x_{i}+b))
$$
原问题是
$$
\min_{w,b}\max_{\alpha} L(w,b,\alpha)
$$
对偶问题则是
$$
\max_{\alpha}\min_{w,b} L(w,b,\alpha )
$$
那么，首先解决内层的最优化，上式对 $w, b$ 偏导得 0 有：
$$
\begin{align*}
\nabla_{b} L(w,b,\alpha) &= 0 \Rightarrow \sum_{i} \alpha_{i}y_{i} = 0\\
\nabla_{w}L(w,b,\alpha) &= 0 \Rightarrow \sum_{i}\alpha_{i}y_{i}x_{i} = w

\end{align*}
$$
将这两个结论代回拉格朗日函数：
$$
\max_{\alpha}L(\alpha_{i}) = \sum_{i}\alpha_{i} -\frac{1}{2} \sum_{i} \sum_{j} \alpha_{i}\alpha_{j} y_{i} y_{j} (x_{i}^{T}x_{j})  
$$
这个问题带有约束条件：
$$
\sum_{i}\alpha_{i}x_{i} = 0
$$
由 KKT 条件中的互补松弛条件，我们继续求解：
$$
\alpha_{i} (1-y_{i}(w^{T}x_{i}+b)) =0 
$$
对于支持向量，我们有：
$$
1-y_{i}(w^{T}x_{i}+b) = 0
$$
求解这个式子需要一点点小技巧：两侧同时乘以 $y_{i}$
$$
y_{i} - y_{i}^{2}(w^{T}x_{i}+b) = 0 \Rightarrow y_{i}-(w^{T}x_{i}+b) = 0 \Rightarrow b = y_{i}-w^{T}x_{i} =y_{i} - \sum_{j} \alpha_{j}y_{j}x_{j}^{T}x_{i} = 0
$$
其中，$j$ 是所有数据点的下标，而 $i$ 是被支持向量指到的数据点的下标

实际求解的过程：**先用带约束的二次规划求出 $\alpha_{i}$，再反代求出 $w,b$ 的值**
求解 $\alpha_{i}$ 的值时，我们有序贯优化算法 (SMO Algo)

## Soft Margin
这种问题是：点无法被两个超平面控制住，因此，我们放松约束，允许一些点掉入到两个超平面的“夹心”中：
$$
y_{i}(w^{T}x_{i}+b) \ge 1- \xi_{i}
$$
因此，我们将优化问题调整一下：
$$
\begin{align*}
\min \frac{1}{2} ||w|| +C\sum_{i} \xi_{i}\\
s.t. y_{i}(w_{i}^{T}x+b) &\ge 1- \xi_{i} 
\end{align*}
$$
从另一个角度，这相当于模型中含有正则化项（注意：正则化项是 $||w||$，代表了我们希望模型尽量简单），而 $C\sum_{i}\xi_{i}$ 则描述了模型与训练集的契合程度

## Kernel Trick
$\forall x, y \in \mathbb{R}^d$ ，一个核函数是一种内积：
$$
K(x,y) = \langle \phi(x),\phi(y)  \rangle
$$
其中，$\phi (\cdot): x \mapsto x^{\dagger}\in\mathbb{H}$ ，也就是一个低维向着无穷维（高维）的映射。我们使用的核函数是正定核函数，这种核函数满足：对于 $x_{1},\cdots, x_{n} \in \mathbb{R}^{d}$，其映射后的高维向量 $\phi (x_{1}),\cdots,\phi (x_{n}) \in \mathbb{H}$ 组成的 Gram 矩阵正定。
为了减少运算步骤（这会使得数学上的不严谨），我们可以将核函数直接写成 $x, y \mapsto \mathbb{R}$ 的函数
- 多项式核：$$
K(x,y) = [\langle  x,y \rangle +1]^{d}
$$
- 高斯核
$$
K(x,y) = \exp(-\frac{||x-y||^{2}}{2\sigma^{2}})
$$
- Sigmoid 核
$$
K(x,y) = \tanh (\beta x_{i}x_{j}+\theta)
$$
核函数的用法是，代替二次规划中的内积运算。

## 求解算法：SMO
**序贯**最小化优化算法每次试图选择两个变量，而将其他变量固定。此时，优化问题就被简化：
![[Pasted image 20230328160800.png]]

首先我们来研究 $\alpha_{1}$ 和 $\alpha_{2}$ 的界：
$\alpha_{1}$ 和 $\alpha_{2}$ 之间存在约束：
$$
\alpha_{1}y_{1}+\alpha_{2}y_{2} = k
$$
考虑 $\alpha_{1},\alpha_{2}$ 同号的情况：那么，
$$
\alpha_{1}+\alpha_{2} = k
$$
那么，我们先考虑把问题转换成关于 $\alpha_{2}$ 的最优化问题，也就是说：
$$
\alpha_{1} = k-\alpha_{2}
$$
这里有约束：
$$
0 \le k -\alpha_{2} \le C
$$
也就是说：
$$
k- C \le \alpha_{2} \le K
$$
同时，$\alpha_{2}$ 自身又满足：
$$
0 \le \alpha_{2} \le C
$$
因此，$\alpha_{2}$ 在变化过程中受到的约束就是：
$$
\max (k-C,0) \le \alpha_{2} \le \min(K,C)
$$
或者你可以直观地从图上来理解：$\alpha_{1}+\alpha_{2} = k$ 实际上是说 $\alpha_{1},\alpha_{2}$ 要在一条直线上动，然后它们会被限制在一个方形区域内，你可以通过看图得到界。

- 使用某种迭代公式更新 $\alpha_{1},\alpha_{2}$，变量的选择使用启发式的方法：第一个变量使得违反 KKT 条件最显著，第二个变量使得变量的变化最大。





==GPT== 
核函数（Kernel Function）是一种数学函数，用于将非线性可分数据映射到高维空间，使其在该空间中变得线性可分。核函数通常用于支持向量机（SVM）等机器学习算法中。

在支持向量机中，核函数被用于计算两个样本之间的相似度。如果两个样本非常相似，它们在高维空间中的距离会很小，否则距离会很大。通过使用核函数来计算相似度，可以将低维度空间中线性不可分的数据转换为高维度空间中线性可分的数据。

常见的核函数包括线性核函数、多项式核函数、高斯核函数等。其中，高斯核函数是最常用的核函数之一，它可以将数据映射到无限维空间，因此可以很好地处理非线性可分问题。

***USER***
如何利用核函数计算相似度？

==GPT==
使用核函数计算相似度的一般步骤如下：

1. 选择合适的核函数。常用的核函数包括线性核函数、多项式核函数、高斯核函数等，不同的核函数适用于不同的数据类型和问题。

2. 将原始数据集映射到高维空间。对于每个样本，将其用核函数映射到高维空间，得到一个向量，该向量的维度取决于所选择的核函数。

3. 计算相似度。在高维空间中，可以通过计算两个向量之间的内积来计算它们的相似度，也可以使用其他的相似度度量方法。

4. 应用机器学习算法。使用相似度来训练机器学习模型，比如支持向量机等。

以高斯核函数为例，其公式如下：

$$K(\boldsymbol{x_i},\boldsymbol{x_j}) = \exp\left(-\frac{||\boldsymbol{x_i}-\boldsymbol{x_j}||^2}{2\sigma^2}\right)$$

其中，$\boldsymbol{x_i}$ 和 $\boldsymbol{x_j}$ 是数据集中的两个样本，$||\boldsymbol{x_i}-\boldsymbol{x_j}||^2$ 是两个样本之间的欧几里得距离的平方，$\sigma$ 是高斯核函数的参数。

使用高斯核函数计算两个样本之间的相似度，即将两个样本用高斯核函数映射到高维空间，然后计算它们在高维空间中的内积。内积的值越大，表示两个样本在高维空间中越相似，相似度也就越高。






当然可以。这里是使用 LaTeX 书写的 SMO 算法中涉及的公式：

1.  计算误差E： $E_i = f(x_i) - y_i$ 其中，$f(x_i) = \sum_{j} (\alpha_j y_j K(x_i, x_j)) + b$ $K(x_i, x_j)$ 是核函数。
    
2.  计算α2的新值（未剪辑）： $\alpha_{2_new_unc} = \alpha_{2_old} + \frac{y_2 (E_1 - E_2)}{\eta}$ 其中，$\eta = K_{11} + K_{22} - 2 K_{12}$，是用于优化α2的步长。
    
3.  计算α2的新值（剪辑后）： $\alpha_{2_new} = \begin{cases} H, & \text{if}\ \alpha_{2_new_unc} > H \ \alpha_{2_new_unc}, & \text{if}\ L \leq \alpha_{2_new_unc} \leq H \ L, & \text{if}\ \alpha_{2_new_unc} < L \end{cases}$ 其中，L 和 H 是剪辑边界，取决于约束条件：如果 $y_1 \neq y_2$： $L = max(0, \alpha_{2_old} - \alpha_{1_old})$ $H = min(C, C + \alpha_{2_old} - \alpha_{1_old})$ 如果 $y_1 = y_2$： $L = max(0, \alpha_{1_old} + \alpha_{2_old} - C)$ $H = min(C, \alpha_{1_old} + \alpha_{2_old})$
    
4.  更新α1： $\alpha_{1_new} = \alpha_{1_old} + y_1 y_2 (\alpha_{2_old} - \alpha_{2_new})$
5. 更新阈值 b： $b_{1_new} = b_{old} - E_1 - y_1 (\alpha_{1_new} - \alpha_{1_old}) K_{11} - y_2 (\alpha_{2_new} - \alpha_{2_old}) K_{12}$ $b_{2_new} = b_{old} - E_2 - y_1 (\alpha_{1_new} - \alpha_{1_old}) K_{12} - y_2 (\alpha_{2_new} - \alpha_{2_old}) K_{22}$ 如果 $0 < \alpha_{1_new} < C$： $b_{new} = b_{1_new}$ 如果 $0 < \alpha_{2_new} < C$： $b_{new} = b_{2_new}$ 否则： $b_{new} = \frac{b_{1_new} + b_{2_new}}{2}$


$$f (x_i) = \sum_{j} (\alpha_j y_j K (x_i, x_j)) + b$$
代表了决策边界
