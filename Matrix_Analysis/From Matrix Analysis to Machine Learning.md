#MA  

## 随机变量的线性变换 
我们用线性代数语言重构一些随机变量的线性变换。为了方便书写，以二元随机变量为例
如果 $Y$ 是由两个随机变量组合而来的，也就是说：
$$
Y = [a \ b]\begin{bmatrix}X_{1} \\ X_{2}\end{bmatrix}
$$
期望的变换：
$$
E(Y) = [a\ b] \begin{bmatrix}E(X_{1})  \\ E(X_{2})\end{bmatrix}
$$
方差的变换：
$$
\mathrm{var}(Y) = [a\ b] \Sigma \begin{bmatrix}a \\ b\end{bmatrix}
$$
高维随机变量的情况：
考虑 $D$ 维的随机变量 $\zeta = [z_{1}, z_{2},\cdots ,z_{D}]^{T}$ 服从多元高斯分布，也就是说，$\mu_{\zeta} = [0,0,\cdots ,0]^{T},\mathrm{var} = \mathrm{diag}(1,1,\cdots,1)$ ，我们使用一个矩阵 $V$ 表征对各个随机变量进行线性组合，使用向量 $\mu= [\mu_{1},\mu_{2},\cdots,\mu_{n}]$ 对均值进行偏移，那么我们得到一个多维随机变量：
$$
\chi  = \begin{bmatrix}x_{1} \\ x_{2} \\ \cdots  \\ x_{n}\end{bmatrix} = V^{T}\begin{bmatrix}z_{1} \\ z_{2} \\ \cdots \\ z_n\end{bmatrix}+\begin{bmatrix}\mu_{1} \\ \mu_{2} \\ \cdots \\ \mu_{n}\end{bmatrix}
$$
$V$ 的一列代表着对 $z_{i}$ 的一种线性组合，那么我们可以推导 $\chi$ 的协方差矩阵：
$$
\begin{align*}
 \mathrm{cov}(\chi ,\chi )\\
&= \mathrm{E}(\frac{(\chi -\mu_{\chi} )(\chi - \mu_{\chi} )^{T}}{n})\\
 &=\mathrm{E}( V^{T}\frac{\zeta\zeta^{T}}{n}V)\\
&= V^{T}I V \\
 &= V^{T}V
\end{align*}
$$
那么，我们推广到一般情况，对于 $n$ 维的随机变量 $\chi$ 和 $\gamma$ 之间满足一个线性映射关系：
$$
\gamma = A\chi 
$$
那么质心：
$$
\mu_{\gamma} = A \mu_{\chi}
$$
协方差：
$$
\mathrm{var}(\gamma) = \Sigma_{\gamma}  = A \Sigma_{\chi} A^{T}
$$
## 数据矩阵向着指定列向量的投影
这个投影被定义为：
$$
y  =Xv = \sum x_{i}v_{i}
$$
其中，$x_{i}$ 是 $X$ 矩阵的一个列向量，那么，从几何直观意义上说，这就是将 $X$ 的各个列向量线性组合起来。

