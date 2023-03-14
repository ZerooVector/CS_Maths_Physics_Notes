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


