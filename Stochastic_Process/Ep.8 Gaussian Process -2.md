#StochasticProcess 

## 高斯过程与高斯分布的引入
### 高斯分布
现在我们来定义什么是高斯过程。$\forall n,\forall t_{1}, t_{2},\cdots,t_{n}$，随机过程的取值为 $X = (X(t_{1}),\cdots,X(t_{n}))^{T}$，那么 $X$ 服从 $n$ 维联合高斯分布 $N(\mu,\Sigma)$ 。对于 $n$ 维的高斯分布。我们知道，在 $n=1$ 的情况：
$$
f_{X }(x)= \dfrac{1}{\sqrt{2\pi }\sigma} \exp\left(- \dfrac{(x-\mu)^{2}}{2 \sigma^{2}}\right)
$$
在 $n=2$ 时的情况就已经相当复杂。因此，我们需要引入矩阵和矢量的符号。我们直接给出 $n$ 维的情况：
$$
f_{X}(x) = \dfrac{1}{(2\pi)^\frac{n}{2} (\det \Sigma)^\frac{1}{2} } \exp\left(- \dfrac{1}{2} (x-\mu)^{T}\Sigma^{-1}(x-\mu) \right)
$$
这里的 $\mu$ 是均值，$\Sigma$ 是协方差矩阵。我们来做一个简单的验证：这是一个概率密度。我们完成积分：
$$
\begin{align*}
I 
&=  \dfrac{1}{(2\pi)^\frac{n}{2} (\det \Sigma)^{\frac{1}{2} }}\int \exp\left(- \dfrac{1}{2} (x - \mu)^{T} \Sigma^{-1}(x-\mu) \right)dx\\

\end{align*}
$$
注意到 $\Sigma$ 是对称矩阵，那么：
$$
\Sigma = U^{T} \Lambda U
$$
其中，$U$ 是正交矩阵，而 $\Lambda$ 是对角阵，从而，显然：
$$
\Sigma^{-1} = U^{T} \Lambda^{-1} U = U^{T} \Lambda^{-\frac{1}{2}}\Lambda^{-\frac{1}{2}} U = B^{T}B
$$
 那么：
 $$
\begin{align*}
I\\
&= \dfrac{1}{(2\pi)^\frac{n}{2} (\det \Sigma)^{\frac{1}{2} }} \int \exp\left(- \dfrac{1}{2} (x - \mu)^{T} B^{T} B(x-\mu)\right)dx \\
&=  \dfrac{1}{(2\pi)^\frac{n}{2} (\det \Sigma)^{\frac{1}{2} }}\int \exp\left(- \dfrac{1}{2} Y^{T}Y\right)  (\det \Sigma)^{- \frac{1}{2}} dy  \\\\
&= \dfrac{1}{(2\pi)^{\frac{n}{2}}}\int \exp \left(- \frac{1}{2}\sum y_{k}^{2}\right)dy_{1} \cdots dy_{n} \\
&= \prod_{k} \dfrac{1}{\sqrt{2 \pi}} \left(\int \exp(- \frac{1}{2} y_{k}^{2})\right)dy_{k} = 1

\end{align*}
$$
其中，在积分换元时，我们利用了
$$
dx= \dfrac{\partial x}{\partial y} dy  = |\det B|^{-1} dy  = ((\prod  \lambda_{k})^{- \frac{1}{2}})^{-1} dy = (\det \Sigma)^{- \frac{1}{2}} dy  
$$

### 高斯分布的生成函数
我们接下来介绍一个适合处理高斯分布的工具：生成函数/特征函数。我们定义：
$$
\Phi_{X}(\omega) = \mathrm{E}( \exp (i \omega^{T}X))
$$
我们试着计算高斯分布的特征函数。
$$
\begin{align*}
\Phi_{X}(\omega) &= \dfrac{1}{(2 \pi)^{\frac{n}{2}}\sqrt{\det \Sigma} } \exp\left(- \dfrac{1}{2} (x - \mu)^{T}\Sigma^{-1} (x-\mu)\right) \exp(i \omega^{T}x)dx\\
&= 
\end{align*}
$$
这个东西有个阴间的做法，我们直接把它搞成一维的。在一维的情况下，我们看看 $\exp(\cdot)$里面有什么，并且进行配方：
$$
- \dfrac{1}{2\sigma^{2}} (x - \mu )^{2} + i \omega x = - \dfrac{1}{2 \sigma^{2}} (x - \mu - i \sigma^{2} \omega)^{2}+ i \omega \mu - \dfrac{1}{2} \sigma^{2} \omega^{2}
$$
对于 $n$ 维的情况，我们可以类比一下：
$$
- \dfrac{1}{2}(x - \mu)^{T} \Sigma^{-1}(x - \mu) + i \omega^{T} x  = -  \dfrac{1}{2} (x - \mu - i \Sigma \omega)^{T} \Sigma^{-1}(x - \mu - i \Sigma \omega) + i \omega^{T }\mu  - \dfrac{1}{2} \omega^{T} \Sigma \omega
$$
此时，很容易完成积分得到：
$$
\Phi_{X}(\omega) = \exp(i \omega^{T}\mu  - \dfrac{1}{2}\omega^{T} \Sigma \omega)
$$

### 高斯分布的性质
高斯分布有一些性质：
- 线性性：如果取
$$
X \in \mathbb{R}^{n}, X \sim N(\mu , \Sigma) , A  \in  \mathbb{R}^{m \times n } 
$$
令 $Y = AX$，那么：
$$
Y \sim N(A \mu, A \Sigma A^{T})
$$
这是一个十分宽泛的条件。我们完全不需要要求 $X,Y$ 同维度，更不会要求 $A$ 是一个一一映射。我们现在使用特征函数探究这个问题，也就是说，我们直接来计算 $Y$ 的特征函数：
$$
\begin{align*}
\Phi_{Y}(\omega) &=  \mathrm{E}(\exp (i \omega^{T}AX ))\\
&= \mathrm{E}(\exp(i (A^{T} \omega)^T X))\\
&= \Phi_{X}(A^{T} \omega)\\
&= \exp(i(A^{T} \omega)^{T} \mu - \dfrac{1}{2} (A^{T} \omega)^{T}\Sigma(A^{T} \omega)\\
&= \exp(i \omega^{T}A \mu - \dfrac{1}{2}\omega^{T}A \Sigma A^{T} \omega)
\end{align*}
$$
从而得证。

>[!EXAMPLE]
>取 $X = (X_{1},\cdots, X_{n})^{T} \sim N$，取 $\tilde X = (X_{n_{1}},\cdots,X_{n_{k}})$，那么，$\tilde X$ 也服从高斯分布。这是显然的。
>但是，假如边缘是高斯分布，联合分布一定是吗？我们举个反例：
> $$f(x_{1},x_{2}) = \dfrac{1}{2 \pi} \exp\left(- \dfrac{1}{2}(x_{1}^{2} + x_{2}^{2})\right)+ g(x_{1},x_{2})$$
> 只要使得 
> $$\int g dx_{1} = \int g dx_{2} = 0$$
> 即可。这样的函数太多太多，例如，我们直接取：
> $$f(x_{1},x_{2}) = \dfrac{1}{2\pi}\exp (- \dfrac{1}{2}(x_{1}^{2} + x_{2}^{2}))(1 +  \sin x_{1} \sin x_{2})$$

我们给出一个判据：$X \sim N$，当且仅当：
$$
\forall  \alpha \in  \mathbb{R}^{n} , \alpha^{T}X \sim N
$$
考虑计算 $X$ 的特征函数：
$$
\Phi_{X}(\omega) = \mathrm{E}(\exp( i \omega^{T} X)) = \Phi_{\omega^{T}X} (1) = \exp(i \cdot 1 \cdot \mu_{\omega^{T}X} - \dfrac{1}{2} \sigma_{\omega^{T}X} \cdot 1^{2})
$$
我们主要计算其中的 $\sigma$，那么：
$$
\sigma - \mathrm{E}(\omega^{T}X - \omega^{T} \mu_{X })= \mathrm{E}(\omega^{T} (X - \mu_{X})(X - \mu_{X})^{T}\omega)   = \omega^{T}\Sigma_{x} \omega
$$
代入原式，立即完成证明。

另一个性质：如果 $X = (X_{1},\cdots, X_{n})^{T} \sim N$ ，且 $X_{1},\cdots X_{n}$ 不相关，那么它们独立。
容易看出，在此时：
$$
\Sigma_{ij} = \mathrm{E}(X_{i}X_{j}) - \mathrm{E}(X_{i}) \mathrm{E}(X_{j}) = 0
$$
也就是说协方差矩阵是对角阵。那么：
$$
f(X) = \prod_{k} \dfrac{1}{\sqrt{2\pi} \sigma_{k}} \exp\left(- \dfrac{(x_{k} - \mu_{k})}{2 \sigma_{k}^{2}}\right)= \prod_{k} f(x_{k}) 
$$
从而得证。
那么，对于高斯分布来说，主成分分析的效果相当于独立成分分析（ICA）。
另外，我们说明构造任意高斯分布的方法。我们取标准的高斯随机变量 $X \sim N(0,I)$，那么我们可以构造 $\tilde X = \Sigma^{ \frac{1}{2}} (X + \Sigma^{- \frac{1}{2}} \mu )$ ，那么，$\tilde X$ 就服从 $N(\mu,\Sigma)$ 分布。

>[!EXAMPLE]
>假定我们有随机变量 $X_{0},\cdots ,X_{N}$，令：
> $$X_{k}= \sqrt{1 - \alpha_{k}} X_{k-1} + \sqrt {\alpha_{k}} \epsilon_{k}$$
> $\epsilon_{k} \sim N(0,I)$ 是独立的。求 $X_{N}$ 的分布。
> 首先，很容易知道 $X_{N}$ 服从高斯分布。令 $\beta_{k} = 1 - \alpha_{k}$，那么：
> $$X_{k}= \sqrt{\beta_{k}} X_{k-1} + \sqrt {1 - \beta_{k}} \epsilon_{k}$$
> 我们可以递推一步： $$X_{k}= \sqrt{\beta_{k}\beta_{k-1}} X_{k-2} + \sqrt{\beta_{k}} \sqrt{1 - \beta_{k}} \epsilon_{k-1} + \sqrt{1 -\beta_{k}} \epsilon_{k}$$
> 后面的随机项服从 $N(0,\sqrt{1 - \beta_{k}\beta_{k-1}}I)$。继续递推即可得到最终结果：令
> $$\bar \beta = \prod \beta_{k}$$
> 那么：
> $$X_{N} = \sqrt{\bar \beta } X_{0}+ \sqrt{1 - \bar \beta}\epsilon_{k}$$

















