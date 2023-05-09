#MA  

## Gram 矩阵

##### Def 幺正空间中的 Gram 矩阵
给出向量组 $\beta_{1},\beta_{2} ,\cdots,\beta_{n}$，拼成一个矩阵 $[\beta_{1},\beta_{2},\cdots ,\beta_{n}]$，那么：
$$
G(\beta) = B^{H}B
$$
容易注意到，$G_{ij} = \beta_{i}^{H}\beta_{j}$，这就是两个向量的标准内积。因此，矩阵乘法 $B^{H}B$ 的结果就是 $B$ 列向量的 Gram 矩阵 

##### Example 函数空间中的 Gram 矩阵
考虑 $\mathcal{F}([a,b],\mathbb{R}^{n})$ ，定义的内积为 $\forall f, g \in \mathcal{F}$:
$$
\langle  f,g \rangle  = \int_{a}^{b}f(t)g(t)dt
$$
因此，$$
G_{ij} = \int_{a}^{b}f_{i}(t) f_{j}(t) dt
$$
## 长度和距离

##### Def 向量的长度和距离
对于向量 $\alpha \in \mathbb{C}^{n}$，其长度（模长）（内积引导出的范数）为：
$$
||\alpha|| = (\langle  \alpha ,\alpha \rangle)^\frac{1}{2}
$$
对于向量 $\alpha ,\beta$，它们的距离定义为：
$$
\mathrm{dis}(\alpha ,\beta) = ||\alpha- \beta ||
$$
实际上，你可以任意地规定一些东西作为长度，只要它们满足以下性质：
- 正性：$||\alpha || \ge 0$，且等号成立当且仅当 $\alpha = 0$
- 正齐性：$||\alpha k|| = |k|\cdot||\alpha||$ 
- 三角不等式：$||\alpha+\beta|| \le ||\alpha||+||\beta||$ 
- Cauchy-Schwartz 不等式：$|\langle  \alpha,\beta \rangle| \le ||\alpha|| \ ||\beta||$
- 平行四边形公式：$||\alpha+\beta||^{2}+||\alpha-\beta||^{2} = 2 (||\alpha||^{2}+||\beta||^{2})$ 

（5）平行四边形公式中，$\alpha+\beta$ 是一条对角线，$\alpha-\beta$ 是另一条对角线。
$$
||\alpha+\beta||^{2} = \langle  (\alpha+\beta),(\alpha+\beta) \rangle = ||\alpha||^{2}+||\beta||^{2}+\langle  \alpha,\beta \rangle + \langle  \beta,\alpha \rangle
$$
$$
||\alpha-\beta||^{2} = ||\alpha||^{2}+||\beta||^{2} - \langle  \alpha,\beta \rangle - \langle  \beta,\alpha \rangle
$$
也就是说，向量长度的第五条是由内积的性质保证的。
只要你把长度定义成内积开根号，第五条就满足。

（4）我们首先给出退化版的证明：假定 $\langle  \alpha,\beta \rangle$ 是实数，C-S 不等式等价于
$$
(2\langle  \alpha,\beta \rangle)^{2} \le  4||\alpha||^{2}\ ||\beta||^{2}
$$
构造一个二次函数
$$
f(t) = at^{2}+bt +c \qquad b  =(2\langle  \alpha,\beta \rangle),a = ||\alpha||^{2},c = ||\beta||^{2} \ \ t \in \mathbb{R}
$$
$f (t) \ge 0$ 就意味着 C-S 不等式成立。注意到
$$
\begin{align*}
f(t) &= \langle  \alpha,\alpha \rangle t^{2}+2\langle  \alpha,\beta \rangle t+\langle  \beta,\beta \rangle\\
 &= \langle  \alpha t,\alpha t \rangle + 2\langle  \alpha t,\beta  \rangle +\langle  \beta,\beta \rangle\\
 &= \langle  \alpha t,\alpha t \rangle + \langle  \alpha t,\beta  \rangle +\langle  \beta ,\alpha t \rangle+\langle  \beta,\beta \rangle\\
 &= \langle  \alpha t+\beta ,\alpha t+\beta \rangle \ge 0
\end{align*}
$$
但是，若 $\langle  \alpha,\beta \rangle$ 不是实数，那么它可以写成
$$
\langle  \alpha,\beta \rangle = |\langle  \alpha,\beta \rangle| \exp (i \theta)
$$
的形式。那么，
$$
\langle  \alpha,\beta \rangle \exp(-i \theta) = |\langle  \alpha,\beta \rangle| = \langle  \alpha\exp (i \theta),\beta \rangle
$$
这样的内积也是实数。利用刚刚证明的结论，$\langle  \alpha',\beta \rangle \le ||\alpha'||\ ||\beta||$ ，又注意到：$|\langle  \alpha',\beta \rangle| = |\langle  \alpha\exp (i \theta),\beta \rangle| = |\langle  \alpha,\beta \rangle|$ ，而且 $||\alpha'||\ ||\beta||  = ||\alpha|| \ ||\beta||$，因此对于这种内积不是实数的情况也是成立的。

注：Cauchy-Schwartz 中，等号成立的条件是 $\alpha$ 和 $\beta$ 线性相关。根据上面的证明过程，如果要求 $\langle  \alpha t+\beta,\alpha t+\beta \rangle=0$，那么就要 $\alpha t+\beta=0$，也就是说，$\alpha$ 和 $\beta$ 线性相关

（3）我们由（4：CS 不等式）推出。将三角不等式两边平方：
$$
\langle  \alpha+\beta,\alpha+\beta \rangle \le ||\alpha||^{2}+2||\alpha||\cdot ||\beta|| +||\beta||^{2}
$$
整理，可知：
$$
\langle  \alpha,\beta \rangle + \langle  \beta,\alpha \rangle \leq ||\alpha||\cdot ||\beta||
$$
注意到式子左侧是一个实数，那么式子的左侧可以改写为：
$$
\mathrm{LHS} = 2\mathrm{Re}\langle  \alpha,\beta \rangle \le |\langle  \alpha,\beta \rangle+\langle  \beta,\alpha \rangle| \le |\langle  \alpha,\beta \rangle|+|\langle  \beta,\alpha \rangle|
$$

##### Theorem 距离的三角不等式
$$
\mathrm{d}(\alpha ,\beta ) \le \mathrm{d}(\alpha,\gamma)+\mathrm{(\beta,\gamma)}
$$
这很容易得证，因为，$(\alpha-\beta) = (\alpha-\gamma)+(\gamma-\beta)$，之后使用向量长度的三角不等式即可。

## 夹角和正交
##### Def 实内积空间的夹角
考虑 $\alpha$ 和 $\beta$ 都是非零向量，那么，它们的夹角被定义为：
$$
\theta(\alpha,\beta) = \arccos \frac{\langle  \alpha,\beta \rangle}{||\alpha||\cdot||\beta||}
$$
C-S 不等式保证了这样的定义是合法的。而且，显然，这个定义只能在实内积空间中完成。

反过来，我们可以使用长度和夹角计算内积：
$$
\langle  \alpha,\beta \rangle = ||\alpha|| \cdot ||\beta|| \cos \theta(\alpha,\beta)
$$

##### Def 正交垂直，复内积
我们称 $\alpha,\beta$ 垂直，则
$$
\langle  \alpha,\beta \rangle = 0
$$
注意：如果在实内积空间内，$\alpha,\beta \not = 0$，那么垂直等价于二者的夹角为 $\pi/2$ 。

##### Theorem 勾股定理的推广
在实内积空间中，以下等价：
- $\alpha$ 与 $\beta$ 垂直
- 夹角为 $\pi/2$ 
- 内积为 0
- $||\alpha+\beta||^{2}= ||\alpha||^{2}+||\beta||^{2}$
- $||\alpha-\beta||^{2}= ||\alpha||^{2}+||\beta||^{2}$

在复内积空间中，以下等价：
- （1）和（3）
- （4）和（5）
- （1）和（3）可以推出（4）和（5），但是不能反推

我们看一看复数的时候，存不存在（4）推（3）
$$
||\alpha+\beta||^{2} = ||\alpha||^{2}+||\beta||^{2} +\langle  \alpha,\beta \rangle +\langle  \beta,\alpha \rangle
$$
显然，就算（4）成立，$\langle  \alpha,\beta \rangle$ 的虚部也可以不为 0

## 内积空间中的最佳逼近问题
问题：$V$ 是 $\mathbb{C}$ 上的内积空间，给出向量 $\beta \in  V$，有限维子空间 $W \subseteq V$，在 $W$ 中求一个元素 $\alpha$，使得
$$
 \min d(\beta,\alpha)  \qquad s.t. \ \beta \in V,\alpha\in W
$$
这也就是所谓的最佳逼近问题。这种问题在模式识别上有重要的应用。显然，子空间中离一个向量最近的，就是这个向量在子空间中的正投影。
![[Ep.12 2023-03-15 14.05.15.excalidraw]]

我们希望找到最优解的存在性、唯一性，以及最优解的求解过程。现在，我们记 $W$ 的基为：$\beta_{1},\beta_{2},\cdots ,\beta_{s}$，通过这样的方法，我们可以将最优解参数化：待求的向量 $\alpha$ 一定可以表示为：
$$
\alpha = \sum_{i=1}^{s} \beta_{i}k_{i}
$$
那么，距离就变成了 $s$ 个变元的函数：$[k_{1}, k_{2},\cdots ,k_{s}] \mapsto d(\beta,\alpha)$  
$$
\mathrm{dis}^{2}(\beta,\alpha) = \langle  \beta - \sum_{j=1}^{s}\beta_{j}k_{j},\beta - \sum_{j=1}^{s}\beta_{j}k_{j} \rangle
$$



























