#StochasticProcess 

我们知道，平稳通常是与某种不变性相联系。在我们之前提到的宽平稳中，我们只关心一阶矩和二阶矩，要求 $\mathrm{E}(X (t)) = m,\mathrm{E}(X (t) X (s)) = R_{X}(t-s)$ 。显然，非平稳的随机过程有无限多种，现在我们只聚焦两种：

## 周期平稳
Cyclostationary（循环平稳 or 周期平稳），我们要求 $R_{X}(t, s) = R_{X}(t+T,s+T)$ ，从而我们可以直接推出 $R_{X}(t, s) = R_{X}(t+nT,s+nT)$
现在，我们希望给定周期平稳的 $X(t)$，将其变回宽平稳。我们假定 $U \sim U [0,T]$，且 $U$ 与 $X(t)$ 独立。只要令 $Y (t) = X(t+U)$（在 $[0,T]$ 的长度内对 $X(t)$ 进行随机的平移），$Y (t)$ 就是宽平稳的，我们将证明这一点：
$$
\begin{align*}
R_{Y}(t,s) \\
&= \mathrm{E}(X(t+U) X(s+U))\\
&= \mathrm{E}_{U}[E_{X}(X(t+U) X(s+U)|U)]\\
&= \mathrm{E}_{U}[R_{X}(t+U,s+U)]\\
&= \dfrac{1}{T} \int_{0}^{T} R_{X}(t+U,s+U) dU \\
&= \dfrac{1}{T} \int_{s}^{s+T} R_{X}(t-s+U',U')dU'\\
&= \dfrac{1}{T} \int_{0}^{T} R_{X}(t-s+U',U')dU'\\
\end{align*}
$$
这里，我们使用了条件期望来处理两个随机变量同时出现的情况。**直观上看，这相当于我们在时间轴上选择一些点，不改变这些点的相对位置，但是允许它们在一个周期内移动。这样利用 $X(t)$ 的周期平稳特性，我们就构造了宽平稳的过程** 

我们稍微聊聊条件期望。假定我们有随机变量 $X,Y$，那么条件期望可以形式化地写成：
$$
\mathrm{E}(X|Y) = \int  x f_{X|Y} (x|y)dx
$$
首先我们要说明，条件期望是一个随机变量，而不是和正常的期望一样是一个确定值。条件期望的一个重要性质是 $\mathrm{E} (Xg (Y)|Y) = g(Y)\mathrm{E}(X|Y)$。因此，我们常常使用条件期望“各个击破”：$\mathrm{E}(g (X, Y)) = \mathrm{E}_{Y}[\mathrm{E}_{X} (g(X,Y))|Y]$。

>[!EXAMPLE] 
> $X_{1},\cdots,X_{n}$ 是独立同分布随机变量，那么：
> $$E(X_{1}+ \cdots + X_{n}) = n \mathrm{E}(X_{1})$$
> 假定现在我们要求 $\mathrm{E} (\sum_{i=1}^{N} X_{i})$，但是 $N$ 是与 $X_{i}$ 独立的随机变量，那么利用上面条件期望的性质，显然可以得到：
> $$\mathrm{E}\left(\sum X_{i}\right)= \mathrm{E}(N) \mathrm{E}(X_{i})$$
 
>[!EXAMPLE] 脉冲幅度调制
>考虑信号 
> $$X (t) = \sum_{k = - \infty}^{+ \infty} \alpha_{k} \phi(t-kT)$$
> 其中，$\phi$ 称为基带波形，$T$ 被称为符号宽度，$\alpha_{k}$ 是信息位。通常来说，我们假定 $\alpha_{k}$ 是宽平稳的。对于这种调制方式的直观理解是：我们将 $\phi$ 平移 $kT$ 个单位以后乘上信息位即可。接下来我们计算其相关函数：
> $$\begin{align*}
R_{X}(t,s) \\
&= \mathrm{E}[(\sum_{k} \alpha_{k} \phi(t-kT))(\sum_{m} \alpha_{m} \phi(t-mT))]\\
&= \sum_{k} \sum_{m} R_{\alpha}(k-m) \phi(t-kT) \phi(s - mT) \\
\end{align*}$$
那么我们显然可以注意到 $R_{X}(t, s) = R_{X}(t+T,s+T)$，$X(t)$ 周期平稳。
然而，对于通信中的信号而言，有一个随机相位是很正常的。因此，我们现在给信号加一个随机相位。那么此时：$$\begin{align*}R_{X}(t,s) &= \dfrac{1}{T} \int_{0}^{T} \sum_{k} \sum_{m} R_{\alpha} (k-m)\phi(t-kT+U) \phi(s-mT+U)dU \\
&= \dfrac{1}{T} \int_{0}^{T} R_{\alpha} (k-m)\sum_{k} \sum_{m} \phi(t-s-kT+U') \phi(U'-mT) dU'\\
&=\dfrac{1}{T} \int_{0}^{T} \sum_{k'} \sum_{m'} R_{\alpha}(k') \phi(t -s - (k'+m')T+U') \phi(U'-m'T) dU'\\
&= \sum_{k'} \sum_{m'} R_{\alpha}(k') \dfrac{1}{T} \int_{0}^{T} \phi(t -s - (k'+m')T+U') \phi(U'-m'T) dU'\\
&= \sum_{k'} \sum_{m'} R_{\alpha}(k') \dfrac{1}{T} \int_{-m'T}^{-(m'-1)T} \phi(t-s+U''-k'T) \phi(U'')dU''\\
&= \sum_{k'} R_{\alpha}(k') \dfrac{1}{T} \int_{-\infty}^{+\infty} \phi(U'') \phi(U''+t-s-k'T)dU''\\
&= \sum_{k'} R_{\alpha}(k') \dfrac{1}{T} R_{\phi}  (t-s-K'T)
\end{align*}$$
其中，我们首先利用了换元 $k' = k - m ,m' = m$，又利用了换元 $U- m'T = U''$。其中的 $R_{\phi}$ 是信号的时间相关，定义为：$R_{\phi}(\tau) = \int_{-\infty}^{+\infty} \phi (U'') \phi (U''+ \tau) dU''$ 。做到这里，我们已经可以明显地看出加入了随机相位的信号是一个宽平稳的过程。
接下来，我们会在频域上看一下：$$\begin{align*} S_{X}(\omega)\\
&= \dfrac{1}{T} \sum_{k'} R_{\alpha}(k') \int R_{\phi} (\tau - k'T) \exp(- i \omega t)d \tau\\
&= \dfrac{1}{T} \sum_{k'} R_{\alpha}(k') \exp(- ik' \tau \omega) \int R_{\phi} (\tau') \exp(- i \omega \tau') d \tau'\\
&= \dfrac{1}{T} S_{\alpha} (T \omega) S_{\phi}(\omega )
\end{align*}$$
这一信号的谱特性是基带信号谱特性和所搭载的信息的谱特性的乘积。

## 正交增量
Orthogonal Increment（正交增量过程）中，我们要求 $X (0) = 0$，任取 $t_{1}\le t_{2} \le t_{3} \le t_{4}$，两个增量 $X (t_{4})- X(t_{3})$ 与 $X (t_{2}) - X(t_{1})$ 之间是正交的，也就是它们的相关为 0。我们取 $s<t$ 进行计算：
$$
\begin{align*}
R_{X}(t,s) &= \mathrm{E}(X(t) X(s))\\
&= \mathrm{E}[(X(t) - X(s) + X(s)),X(s)]\\
&= \mathrm{E}[(X(t) - X(s))X(s)] + \mathrm{E}[X^{2}(s)]\\
&= \mathrm{E}[X^{2}(s)]
\end{align*}
$$
显然，这不是宽平稳的。如果 $s,t$ 的大小不定，那么 $R_{X}(t, s) = \mathrm{E}[X^{2}(\min(s,t))]$。我们现在要说明，如果 $R_{X}(t,s)$ 是 $s,t$ 中最小值的那个函数，那么此随机过程必定有正交增量。（直观上，这说明 $(0,s)$ 一段与 $(s,t)$ 一段根本没有任何关系，因此 $(0, s)\ (0,t)$ 做相关的时候， $(s,t)$ 一段完全被排除在外）
$$
\begin{align*}
E[(X(t_{4} )- X(t_{3}))(X(t_{2}) - X(t_{1}))]\\
&= R_{X}(t_{4},t_{2}) - R_{X}(t_{3},t_{2}) + R_{X}(t_{3},t_{1})- R_{X}(t_{4},t_{1})\\
&= g(t_{2}) - g(t_{2}) + g(t_{1}) - g(t_{1})\\
&= 0 
\end{align*}
$$
现在，我们也来构造一个平稳的过程 $Y(t)$。只需要：
$$
Y(t) = \dfrac{\mathrm{d}}{\mathrm{d}t} X(t) = \lim_{\Delta \rightarrow 0 } \dfrac{X(t + \Delta ) - X(t)}{\Delta }
$$
我们来验证这一点：
$$
\begin{align*}
R_{Y}(t,s) \\
&= \mathrm{E}\left(\dfrac{\mathrm{d}}{\mathrm{d}t} X(t) \dfrac{\mathrm{d}}{\mathrm{d}t}X(s)\right)\\
&= \dfrac{\partial^{2} }{\partial t \partial s } \mathrm{E}(X(t)X(s)) \\
&= \dfrac{\partial ^{2}}{\partial t \partial s }R_{X}(t,s)\\
&= \dfrac{\partial^{2} }{\partial t \partial s} R_{X}(min(s,t))
\end{align*}
$$
为了简化，我们首先考虑一个重要的随机过程：布朗运动
- $B (0) = 0$
- 正交增量
- $B (t) - B (s) \sim N(0,\sigma^{2}t)$
那么它的相关函数是 $R_{B}(t, s) = \mathrm{E}[B^{2} (\min (t, s))] = \sigma^{2} \min(t,s)$ ，那么根据上面的分析，可以得到 $R_{Y} = \sigma^{2} \delta(t-s)$。
（注：我们暂时约定绝对值的求导 $\dfrac{\mathrm{d}}{\mathrm{d}x} |x| = \mathrm{sign}(x)$，符号函数的求导 $\dfrac{\mathrm{d}}{\mathrm{d}x }\mathrm{sign}(x) = 2 \delta (x)$） 
因此，$Y(t)$ 是一个白噪声过程。求导是一个高通滤波，那么这就说明我们的正交增量过程经过高通滤波以后，平稳分量被分离出来。








