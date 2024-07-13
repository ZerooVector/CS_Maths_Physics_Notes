#StochasticProcess 

## 检验悖论的介绍
我们回到上节课的问题。我们知道，$S_{n}-S_{n-1} = T_{n} \sim \exp (\lambda)$。我们考虑时间点 1 周围的两个事件：$N(1)$ 和 $N(1)+1$。那么我们现在希望计算 $S_{N (t)+1} - S_{N (t)}= T$。一个计算方法是：
$$
\begin{align*}
T &= P(S_{N+1} - S_{N}<t)\\
&= \sum P(S_{N+1} - S_{N}<t|N(t)=n )P(N(t)=n)\\
&= \sum (1 - \exp(- \lambda t)) P(N(t)=n)\\
&= 1- \exp(-\lambda t) 
\end{align*}
$$
这对吗？为什么还是指数分布呢？显然还是有矛盾，但是问题究竟出在哪？主要问题是对 $P (S_{N+1} - S_{N}<t|N (t)=n )$ 的理解有问题。$N(t)=n$ 的条件影响了前面时间间隔的分布。

我们先给一个简单的例子。假定发生事件的次数 $N(t)=1$，我们计算这个事件发生的时间：
$$
\begin{align*}
F_{s |N(t) = 1}(s|N(t)=1)&= \dfrac{P(T<s,N(t)=1)}{P(N(t)=1)}\\
&= \dfrac{P(N(s)=1,N(t)-N(s)=0)}{P(N(t)=1)}\\
&= \dfrac{P(N(s)=1)P(N(t-s)=0)}{P(N(t)=1)}\\
&= \dfrac{s}{t}
\end{align*}
$$
也就是说，如果我们知道第一个事件在 $t$ 时刻已经发生了，那么它发生的时间就是 $[0,t]$ 上的均匀分布！接下来，我们介绍泊松分布中的 **Inspection Paradox**。

我们假设在 $t$ 时刻来观察这个泊松过程，但是我们不知道此时发生了几次事件，也就是不知道 $N(t)$。我们将 $t$ 时刻到之后第一个事件发生的这段时间间隔叫做 $A(t)$，$t$ 时刻到之前一个时间发生的时间间隔叫做 $B(t)$。那么显然有：
$$
A(t) = S_{N(t)+1} - t \quad B(t) = t - S_{N(t)}
$$
我们现在开始计算：
$$
\begin{align*}
P(A(t)>x,B(t)>y)\\
&= P(N[t-y,t+x]=0)\\
&= \exp(-\lambda(x+y)) 
\end{align*}
$$
立刻得到：
$$
P(A(t)>x) = \exp(- \lambda x) \quad P(B(t)>y) = \exp( - \lambda y)
$$
因此，前后两段时间都是指数分布，并且互相独立。但是注意 $B(t)$ 是被截断的。检查悖论的直观解释是：当我们试图计算 $A(t)+B(t)$ 时，我们并不是选择了一个区间，对这个固定区间的长度进行观测；我们是选择了一个时间点，对覆盖了这个时间点的区间的长度进行观测。显然，更长的区间有更高的概率覆盖被我们选中的时间点。


## 事件发生时间点的条件分布
我们现在研究一个问题：一段时间内发生 $n$ 次事件，这 $n$ 次事件的发生时间是如何分布的？
$$
\begin{align*}
F_{s_{1},\cdots ,s_{n}} (x_{1},\cdots ,x_{n})&= P(s_{1}< x_{1},\cdots ,s_{n}<x_{n}|N(t)=n)\\
&= 
\end{align*}
$$
为了处理这个问题，我们需要介绍顺序统计量。如果 $X_{1},\cdots ,X_{n}$ 独立同分布，我们对这 $n$ 个随机变量进行排序：令 $X_{(1)} = \min (X_{1},\cdots, X_{n}),\cdots ,X_{(n)} = \max(X_{1},\cdots,X_{n})$ ，我们现在希望求出 $X_{(1)},\cdots,X_{(n)}$ 的分布。显然我们可以看出：
$$
F_{X_{(n)}} = \prod P(X_{i}<x) = (F_{X_{1}})^{n}
$$
$$
F_{X_{(1)}} =1 - \prod P(X_{i}>x) = 1 - (1- F_{X_{1}})^{n}
$$
我们计算中间的部分。这里遇到的最严重的问题是：第 $k$ 个随机变量小于 $x$，但是你说不清楚 $[0,x]$ 之间到底有多少个。所以我们换一个神奇的方法：
$$
\begin{align*}
P(x < X_{(k)}<x + \Delta x) &= C_{n}^{k-1}C_{n-k+1}^{n-k}(F_{X}(x))^{k-1}(1-F_{X}(x+\Delta x))^{n-k}f_{X}(x) \Delta x
\end{align*}  
$$
当我们所取的区间足够小，区间内就只有一个随机变量，避免对多种情况分类讨论，反复求和。
我们可以继续使用微元法来得到联合分布：
$$
f_{X_{(k)},X_{(m)}} (x_{k},x_{m}) = C_{k-1}^{n} C_{n-k+1}^{1}C_{n-k}^{m-k-1}C_{n-m+1}^{1}C_{n-m}^{n-m} (F_{X}(x_{k}))^{k-1}(F_{X}(x_{m}) -F_{X}(x_{k}))^{m-k-1}(1-F_{X}(x_{m}))^{n-m} f_{X}(x_{k})f_{X}(x_{m})
$$
继续，我们将求出 $n$ 个次序统计量的联合分布：
$$
f(x_{1},\cdots,x_{n}) = n! \prod (f(x_{i}))
$$

我们现在用类似的思想来分析泊松过程中的问题。先考虑一个简单的：
$$
\begin{align*}
f_{s_{1},s_{2}}(x_{1},x_{2}|N(t)= 2) &= \dfrac{1}{\Delta x_{1}\Delta x_{2}} P(x_{1}<s_{1}<x_{1}+\Delta x_{1},x_{2}<s_{2}<x_{2}+\Delta x_{2}|N(t)=2)\\
&= \dfrac{1}{\Delta x_{1}\Delta x_{2}}  P(N(x_{1})=0,N(x_{2}-x_{1}-\Delta x_{1})=0,N(t-x_{2}-\Delta x_{2})=0,N(\Delta x_{1})=1,N(\Delta x_{2})=1|N(t)=2)\\
&= \dfrac{1}{\Delta x_{1}\Delta x_{2}} \exp(-\lambda(t - \Delta x_{1}-\Delta x_{2})) \lambda\Delta x_{1}\exp(- \lambda\Delta x_{1}) \lambda\Delta x_{2}\Delta x_{2} \left(\dfrac{(\lambda t)^{2}}{2!}\exp(- \lambda t)\right)^{-1}\\
&= \dfrac{1}{\Delta x_{1}\Delta x_{2}}  \dfrac{\Delta x_{1} \Delta x_{2}}{t^{2}} 2! \quad 0<x_{1}<x_{2}<t \\
&= \dfrac{2!}{ t^{2}}
\end{align*}
$$

进行相似的计算可以得到：
$$
f(x_{1},\cdots,x_{n}|N(t)=n) = \dfrac{n!}{t^{n}}\quad 0<x_{1}<\cdots<x_{n}<t
$$
注意：这里我们没有像次序统计量一样有一大堆排列组合的系数。这是因为之前计算次序统计量的时候，$X_{1},\cdots X_{n}$ 是无序的，你可以随便排列，使得任意一个随机变量出现在指定的次序上。现在，在泊松过程中，事件的发生有自然的先后顺序，事件 2 只能在事件 1 之后发生。
因此，这个分布就是 $n$ 个均匀分布的随机变量的次序统计量的分布。

出一个脑筋急转弯
>[!QUESTION]
>一个公交车站，$[0,T]$ 内有 $n$ 辆车，间隔是 $T_{1},\cdots,T_{n}$。乘客以泊松过程到达车站。假定每一次发车都可以将乘客全部运走。现在问我应该如何设计发车间隔，从而使得乘客的平均等待时间最小。

我们考虑 $T_{1}$。设每个乘客的到达时间为 $S_{k}$，那么我们需要计算：
$$\begin{align*}
\mathrm{E}\left(\sum_{k}(T_{1} - S_{k})\right) &= \mathrm{E}\left(\sum_{k}T_{1}\right) - \mathrm{E}\left(\sum_{k} S_{k}\right)\\
&= \lambda T_{1}^{2} - \mathrm{E}\left(\sum_{k}S_{k}\right)\\
&= \lambda T_{1}^{2} - \mathrm{E}\left(\mathrm{E}\left(\sum_{k=1}^{N(T_{1})} S_{k}|N(t_{1}) = n\right)\right)\\
&= \lambda T_{1}^{2} - \mathrm{E}\left(\mathrm{E}\left(\sum_{k} U_{k}|N(t)=n\right)\right)\\
&= \lambda T_{1}^{2} - \dfrac{\lambda T_{1}^{2}}{2}\\
&= \dfrac{1}{2} \lambda T_{1}^{2}
\end{align*}$$
所以，这个问题变成了：
$$
\min \dfrac{1}{2} \lambda \sum_{i} T_{i}^{2} \quad \text{s.t.}\sum_{i} T_{i} = T
$$
从而，均匀间隔发车是最好的。

## 过滤泊松过程
我们现在想要挑战一下泊松过程里面独立增量这个性质。根据前面的计算：
$$
G_{N(t+\Delta t)}(Z) - G_{N(t)}(z) = \mathrm{E}(Z^{N(t)}(Z^{N(t+\Delta t)- N(t)})-1)
$$
我们如果做不到独立增量，那么我们就无法算下去。现在，我们希望取消泊松过程中独立增量的性质，建立一个新的模型。在此之前，复合泊松过程、非齐次泊松过程都没有破坏独立增量，这是因为，它们每次计数后触发的“效应”是随着时间不变的。于是，现在，我们使得每次计数的效应都随着时间改变。我们给出这样的模型：
$$
Y(t) = \sum_{k=1}^{N(t)} h_{k}(t) = \sum_{k=1}^{N(t)} h_{k}(t,s_{k},A_{k}) 
$$
其中，$A_{k}$ 是独立同分布的随机变量，而且独立于泊松过程 $N(t)$ 本身。我们现在研究其特征函数：
$$
\begin{align*}
\Phi_{Y(t)} &= \mathrm{E}(\exp(i \omega Y(t))) \\
&= \mathrm{E}\left(\exp\left(i \omega \sum_{k=1}^{N(k)}h_{k}(t,s_{k},A_{k})\right)\right)\\
&= \mathrm{E}\left(\mathrm{E}\left(\mathrm{E}\left(\exp\left(i \omega \sum_{k} h(t,s_{k},A_{k})\right)|\{S_{k}\},N(t)=n\right)|N(t)=n\right)\right)\\
&= 
\end{align*}
$$
我们先把最内层关于 $A_{k}$ 的期望搞出来，令：
$$
B(t,s) = \mathrm{E}(\exp(i \omega h (t,s,A_{k})))
$$
注意，这里利用了 $A_{k}$ 独立同分布的性质，求出期望来才与 $A_{k}$ 无关。继续下面的计算：
$$
\begin{align*}
\Phi_{Y(t)} &= \mathrm{E}(\exp(i \omega Y(t))) \\
&= \mathrm{E}(\mathrm{E} (\prod_{k} B(t,s_{k}) |N(t)=n))\\
&= \mathrm{E}\left(\int_{0}^{t}\cdots\int_0^{s_{3}}\int_{0}^{s_{2}}\prod_{k}B(t,s_{k}) \dfrac{n!}{t^{n}}  ds_{1}\cdots ds_{n} | N(t)=n\right ) \\
&= \mathrm{E}\left(\dfrac{1}{n!} \int_{0}^{t} \cdots \int_{0}^{t} \prod_{k} \dfrac{n!}{t^{n}}B(t,s_{k})ds | N(t)=n \right) \quad \text{利用了B的对称性，B是连乘起来的，积分在s的不同顺序上得到相同结果}\\
&= \mathrm{E}\left(\left(\dfrac{1}{t}  \int_{0}^{t} B(t,s)ds\right)^{N(t)} | N(t)=n \right)\\
&= G_{N(t)}(z) \qquad z = \dfrac{1}{t} \int_{0}^{t} B(t,s)ds \\
&= \exp\left(\lambda  t \left(\dfrac{1}{t}\int_{0}^{t} B(t,s)-1\right)\right)\\
&= \exp\left(\lambda\int_{0}^{t}(E_{A}(\exp(i \omega h(t,s,a)-1))ds)\right)\\
\end{align*}
$$
我们求一下它的期望：
$$
\begin{align*}
E(Y(t)) &= \dfrac{\mathrm{d}}{\mathrm{d} \omega} \dfrac{1}{i} \Phi_{Y(t)}(\omega)\\
&= \lambda \int_{0}^{t}  \mathrm{E}_{A}(h(t,s,A))ds 
\end{align*}
$$

>[!EXAMPLE] 排队论
>排队论用于对服务台进行建模，一个排队模型有三个重要的要素：服务台的个数、每个服务台的服务时间服从的分布、顾客到来的间隔时间服从的分布。我们现在研究 $M/G/\infty$ 排队模型。
现在，我们假定 $Y(t)$ 代表系统内的人数，我们希望求出 $Y(t)$ 的期望。

如果我们将 $Y(t)$ 写成：
$$
Y(t) = \sum_{k} h(t,s_{k},A_{k})
$$
那么，$h$ 是顾客对系统的贡献。显然，顾客只有留在系统内的时候，才对队长有贡献。我们将其进入公园的时间记作 $s_{k}$，矩形窗的长度为 $A_{k}$，那么：
$$

h(t,s_{k},A_{k}) = 
\begin{cases}
1 \quad 0 \le t - s_{k}\le A_{k}  \\
0 \quad others
\end{cases}
$$
代入上面的公式求解即可。注意：在资源受限时，系统内出现纯等待， $A_{k}$ 的分布不再是分布 $G$，而且更重要的是 $A_{k}$ 不再独立，因此上面的整套体系就无法使用了！

