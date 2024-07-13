#StochasticProcess 

今天开始，我们展开随机过程的一个新篇章。在之前，我们研究随机变量之间的线性相关关系，现在，我们要研究一个随机过程的马尔可夫性质。我们现在介绍一种最简单的马尔可夫过程：泊松过程。

我们现在来计数一段时间（$[0,t]$）上某种事件发生的数目。不幸的是，事件之间的间隔往往是随机变量。我们使用 $N(t)$ 代表 $[0,t]$ 内时间的发生次数，显然 $N(t)$ 是个随机过程。我们将这样的随机过程称作计数过程（点过程）。

我们现在的重点不再是计算相关函数，而是计算 $P(N(t)=k)$。我们现在给泊松过程一个定义：
- $N (0) =0$
- 有独立增量
- 有平稳增量
- 稀疏性
注意：前三条已经限制了只有两种随机过程：布朗运动和泊松过程
我们现在将从以上的条件中推出定量的结论，也就是 $N(t)$ 的分布！

我们仍然使用生成函数（矩母函数）来研究这样的离散随机变量。
$$
G_{N(t)}(Z) = \mathrm{E}(Z^{N(t)}) = \sum_{k} z^{k}P(N(t)=k) 
$$
我们现在希望把这个矩母函数做出来。我们的条件与增量有着密切的联系，因此我们也从增量的角度切入。考虑：
$$
\Delta N = N(t + \Delta t) - N(t)
$$
我们希望拿出一个与矩母函数有关的微分方程。我们考虑：
$$
\begin{align*}
G_{N(t+\Delta t)} - G_{N(t)} \\
&= \mathrm{E}(Z^{N(t+\Delta t)}) - \mathrm{E}(Z^{N(t)}) \\
&= \mathrm{E}(Z^{N(t)}(Z^{N(t+\Delta t) - N(t)} - 1))\\
&= \mathrm{E}(Z^{N(t)}) \mathrm{E}(Z^{N(t+\Delta t) - N(t)} - 1) \quad \text{利用了独立增量性质}\\
&= G_{N(t)}(z) \mathrm{E}(Z^{N(\Delta t)}-1) \quad \text{利用了平稳增量性质}\\
&= 
\end{align*}
$$
现在，我们两边同时除以 $\Delta t$：
$$
\begin{align*}
\dfrac{1}{\Delta t} (G_{N(t+\Delta t)} - G_{N(t)})\\
&=  G_{N(t)}(z) \dfrac{\mathrm{E}(Z^{N(\Delta t)}-1)}{\Delta t}\\
&=  G_{N(t)}(z) \dfrac{\sum_{k} Z^{k}P(N(\Delta t)=k)-1}{\Delta t}\\
&= G_{N(t)}(z) \dfrac{P(0)-1+ZP(1)+\sum_{k \ge2}Z^{k}P(k)}{\Delta t}
\end{align*}
$$
我们一点一点看：
$$
\begin{align*}
P(0) &= P(N(s)=0,N(t)-N(s)=0) \ \forall 0<s<t \\
&= P(N(s)=0) P(N(t)-N(s)=0)\\
&= P(N(s)=0)P(N(t-s)=0)\\

\end{align*}
$$
满足这种条件的函数几乎只能是指数函数。我们令 $P (0) = g(\cdot)$，那么 $g$ 的性质是 $g (t+s) = g(t)g(s)$。当然，我们需要说明为什么这样的函数是指数。令 $h = \log g$，但是这里需要证明 $g>0$。注意到：
$$
g(t)= g\left(\dfrac{t}{2}\right)^{2} \ge  0
$$
如果现在存在 $g(t_{0})=0$，那么 $g \left(\dfrac{t_{0}}{2}\right),\cdots ,g\left(\dfrac{t_{0}}{2^{n}}\right)$ 都为 0，从而推出 $g(0)=0$（这里假设 $g$ 是连续的），从而 $g(t)=g(0)g(t)=0$，这只是一个平凡情况，我们不想研究。
那么我们继续回到对于 $h$ 的讨论。$h$ 显然会满足：$h(t+s)=h(t)+h(s)$。我们现在希望说明 $h$ 一定是线性的。首先，我们考虑 $t$ 是正整数的情形，若 $t=n$，那么 $h (n) = h (n-1)+h (1)=h (n-2)+2h (1) =\cdots =nh(1)$；其次，我们考虑 $n$ 都是整数的情形。此时有 $h(0)=h(0)+h(0)$，从而 $h(0)=0$，从而立刻推出 $h(-n)=h(0)-h(n)=-nh(1)$；之后，我们再将其推广到有理数上：$h\left (\dfrac{n}{m}\right) = n \cdot h(\dfrac{1}{m})$ ，又利用 $m h\left (\dfrac{1}{m}\right) = h(1)$，从而 $h\left (\dfrac{n}{m}\right)= \dfrac{n}{m} h(1)$；最后，我们再将其推广到无理数上，由于任意的实数可以被有理数逼近，则 $h (x) = h (\lim_{n \rightarrow\infty} q_{n}) = \lim \lambda q_{n}  = \lambda x$。
到现在，我们终于可以说 $P (0) = \exp(-\lambda t)$。其中我们规定 $\lambda>0$。

在研究剩下两项的时候，我们需要对稀疏性做出说明：时间不能在极短的时间内连续发生，或者，我们也可以说：在极短时间内事件多次发生的概率很低。从而我们考虑第三项。于是我们进行下面的分析：
$$
\begin{align*}
ZP(1)  + \sum_{k\ge2} Z^{k}P(k) =P(1)(Z + \sum_{k \ge2} \dfrac{Z^{k}P(k)}{P(1)})
\end{align*}
$$
我们现在希望给出一个假定。我们显然希望后面 $\sum_{k \ge 2}$ 求和的部分逼近 0，但是我们不希望在这个假定里面把 $Z$ 带进来。我们现在来看看矩母函数中 $Z$ 变换的收敛域：对于 $|Z|\le 1$ 肯定是收敛的，但是其余的我们不知道。我们只在收敛域内分析这个求和。
$$
\begin{align*}
\sum_{k \ge2} \dfrac{Z^{k}P(k)}{P(1)} &\le \sum |Z|^{k}\dfrac{P(k)}{P(1)}\\
&\le \sum \dfrac{P(k)}{P(1)} \\
&= \dfrac{P(N(t)>2)}{P(N(t)=1)}
\end{align*}
$$
我们现在令以上比值在 $\Delta  t \rightarrow 0$ 时趋于 0。到这里，我们才能界定稀疏性。

我们接下来考虑最后一项。显然有：
$$
\begin{align*}
\dfrac{1}{\Delta t} P(1)\left(1+ \dfrac{P(>2)}{P(1)}\right)&= \dfrac{1}{\Delta t} (1-P(0)) 
\end{align*}
$$
从而令 $\Delta t \rightarrow 0$ ，我们就得到了：
$$
\dfrac{P(1)}{\Delta t} = \lambda
$$
接下来回到我们开始时对于矩母函数的研究上去。
$$
\begin{align*}
\dfrac{1}{\Delta t} \mathrm{E}(Z^{N(\Delta t)}-1) \\
&= \dfrac{1}{\Delta t}(P(0)-1) + \dfrac{1}{\Delta  t} P(1) (Z + \sum_{k\ge2}Z^{k}\dfrac{P(k)}{P(1)})\\
&= - \lambda + \lambda Z + 0 \\
&= \lambda(Z-1)
\end{align*}
$$
从而我们可以得到与矩母函数有关的微分方程（注意：$G$ 其实是有 $z,t$ 两个变量，这里是关于 $t$ 的微分方程，把 $z$ 当常数就行）：
$$
\dfrac{G_{N(t)}(z)}{\mathrm{d}t} = G_{N(t)}(z)(\lambda-1)z
$$
初值：$G_{N (0)}(z) = 1$，那么直接得到：
$$
G_{N(t)}(z) = \exp(\lambda t(z-1)) = \exp(z \lambda t) \exp(- \lambda t) = \sum z^{k} \dfrac{(\lambda t)^{k}}{k!} \exp(- \lambda t)
$$
（这里只将含有 $z$ 的第一项展开，以便和矩母函数的形式对应），从而直接看出：
$$
P(N(t)=k) = \dfrac{(\lambda t)^{k}}{k!}\exp(- \lambda t) 
$$
这是泊松分布。从定义中显然直接得到：
$$
P(N(t)-N(s)-k) = \dfrac{(\lambda (t-s))^{k}}{k!}\exp(- \lambda (t-s)) 
$$
由泊松分布的期望：
$$
\lambda = \dfrac{\mathrm{E}(N(t))}{t}
$$
因此，$\lambda$ 被称为“强度”(Intensity)，它指的是单位时间内发生事件的平均次数。同时，泊松分布的方差也是：
$$
\mathrm{Var}(N(t)) = \lambda t
$$
我们现在稍微计算相关函数。
$$
\begin{align*}
\mathrm{E}(N(t)N(s))\\
&= \mathrm{E}((N(t)-N(s)+N(s))N(s))\\
&= \mathrm{E}(N(t)-N(s))\mathrm{E}(N(s)) + \mathrm{E}^{2}(N(s))\\
&= \lambda(t-s) \lambda s+  \lambda s + \lambda^{2}s^{2}\\
&= \lambda^{2} ts + \lambda \min(t,s)
\end{align*}
$$
因此，它并不是宽平稳的。

我们现在考虑另外一件事：事件之间的间隔服从什么？我们研究第一个间隔。
$$
\begin{align*}
P(T_{1} \le t ) &= P(N(t) \ge0)\\
&= 1 - \exp(- \lambda t)\\
\end{align*}
$$
我们这里采用了和布朗运动类似的分析方式，将一个时间和随机过程 $N(t)$ 联系起来。那么我们得到：
$$
f_{T_{1}} (t) = \lambda \exp(- \lambda t)
$$
服从指数分布！（注意：指数分布的无记忆性导致了泊松过程的马尔可夫性）由泊松过程的性质可知，所有事件之间的间隔都是独立同分布的。那么，我们现在希望计算某个事件发生时刻的分布。我们利用特征函数来做这件事情。我们显然可以知道：
$$
S_{k} = \sum_{i=1}^{k} T_{i}  \quad  \rightarrow \quad  \phi(S_{k}) =  \left(\dfrac{1}{\lambda+ i \omega} \right)^{k}
$$
我们可以把这个傅里叶变换做出来，问题就解决了。我们现在换一个方式，从概率的角度解决这个问题。我们知道：
$$
\begin{align*}
P(S_{k} <t) &= P(N(t)\ge k)\\
&= \sum_{n=k}^{\infty} \dfrac{(\lambda t)^{n}}{n!} \exp(- \lambda t)
\end{align*}
$$
从而：
$$
\begin{align*}
f(t) &= \sum_{n=k}^{\infty}\left( \dfrac{\lambda(\lambda t)^{n-1}}{(n-1)! } - \dfrac{\lambda (\lambda t)^{n}}{n!}\right) \exp(-\lambda t)\\
&= \dfrac{\lambda(\lambda t)^{k}}{(k-1)!} \exp(-\lambda t)  \quad  \text{注意：中间的项都消去了}
\end{align*}
$$
这个分布是 Gamma 分布。它来源于 Gamma 函数：
$$
\Gamma (x) = \int_{0}^{\infty} t^{x-1} \exp(-t)dt
$$
我们看看它的性质：
$$
\begin{align*}
\Gamma(n+1) &= \int t^{n} \exp(-t ) dt \\
&= \int t^{n} d (\exp(-t))\\
&= -t^{n}\exp(-t) + n\int \exp(-t)  t^{n-1} dt\\
&= n \Gamma(n) 
\end{align*}
$$
因此，Gamma 函数实际上是对阶乘定义的延申，我们不要求 $n$ 是正整数。

