#StochasticProcess 

我们现在来看看泊松过程的一些推广形式。
### 无平稳增量的情形
我们会发现，在之前的的推导过程中我们大量使用了平稳增量的假设，因此去掉平稳增量之后我们寸步难行！现在我们给一个新的假设，直接针对我们上节课给出的微分方程中的一项：
$$
\dfrac{\lim_{\Delta t \rightarrow 0 }[ 1 - P(N(t + \Delta t) - N(t)=0)]}{\Delta t} = \lambda(t) 
$$
容易按照之前的方式搞出微分方程：
$$
\dfrac{\mathrm{d}}{\mathrm{d} t} G(N(t);z) = G(N(t);z) \lambda(t) (z-1)
$$
这个方程的解是：
$$
G(N(t);z) = \exp\left(- (z-1) \int_{0}^{t} \lambda(s) ds\right) 
$$
用与之前完全相同的手法，可以得到：
$$
P(N(t)=k) = \dfrac{(\int_{0}^{t} \lambda(s)ds )}{k!}\exp\left(-\int_{0}^{t} \lambda(s)ds\right)
$$
我们将这种泊松过程称为非齐次（Non-Homogeneous）泊松过程。显然，泊松过程只是特例，非齐次的泊松过程才是实际。

### 从“计数”到“效应统计”
我们考虑如下的随机过程：
$$
Y(t) = \sum_{k=1}^{N(t)} X_{k}
$$
其中，$N(t)$ 是泊松过程，而 $X_{k}$ 独立同分布。我们仍然计算其矩母函数：
$$
\begin{align*}
G(Y(t);z) &= \mathrm{E}(Z^{\sum X_{k}})\\
&=\mathrm{E}(\mathrm{E}(Z^{\sum X_{k}}|N(t) = n))\\
&= \mathrm{E}(\mathrm{E}^{n}(Z^{X_{1}} )|N(t))\\
&= \mathrm{E}((G_{X_{1}}(z))^{N(t)})\\
&= \mathrm{E}(U^{N(t)})|_{U = G_{X_{1}}(z)} \quad \text{这一步可能看上去不顺眼！但是这只是一个变量替换！}\\
&= G_{N(t)}(u)|_{u = G_{X_{1}}(z)}  \quad \text{这一步是按照矩母函数的定义写出的，就是N的矩母函数在某处的取值！（虽然看起来也不顺眼！）}\\
&= G_{N(t)}(G_{X_{1}}(z))\\
&= \exp(\lambda t (G_{X_{1}}(z)-1))
\end{align*}
$$
由于计算得到的母函数是泊松分布的母函数和 $X_{k}$ 的母函数的复合，因此我们将这种过程称为复合泊松过程。

>[!EXAMPLE]
一些学生以泊松流到达学校，学生中男生所占的比例为 $p$。问如果只计数到达的男生，还是不是一个泊松流？
显然在直观上是的。令 $X_{k}$ 服从两点分布即可，我们直接计算 $Y(t)$ 的母函数：
$$G_{Y(t)}(z) = \exp(\lambda p t(z-1))$$
显然，我们“以貌取人”一下，这就是个泊松分布。这种技术在生活中（尤其是计算机网络中）由重要应用，被称为“随机化”技术。

### 泊松过程的和
假设我们由两个泊松过程。参数分别为 $\lambda_{1},\lambda_{2}$，假定它们互相独立。现在问二者加在一起的效果。我们仍然计算 $N (t) = N_{1}(t)+N_{2}(t)$ 的矩母函数：
$$
\begin{align*}
G_{N(t)}(z)\\
&= \mathrm{E}(Z^{N_{1}+N_{2}})\\
&= \mathrm{E}(Z^{N_{1}}) \mathrm{E}(Z^{N_{2}})\\
&=  G_{N_{1}}(z)G_{N_{2}}(z)\\
&= \exp((\lambda_{1} + \lambda_{2})t (z-1))
\end{align*}
$$
显然容易推广到多个泊松过程相加的情况。

我们考虑一些脑筋急转弯！
>[! QUESTION]
>三个人去银行，银行只有两个柜台。每个柜台对每个顾客的服务时间服从参数为 $\lambda$ 的指数分布。问一开始等待的那个人最后离开银行的概率是多少？

假设两个服务台第一次服务的时间为 $T_{1}\sim \exp (\lambda) ,T_{2} \sim \exp(\lambda)$，那么第一个人被服务完成的时间 $T = \min (T_{1}, T_{2}) \sim \exp (2\lambda)$。
我们一般的无记忆性是：
$$
P(X>x+y|X>x) = P(X>y)
$$
现在，如果 $y$ 是随机变量，那么无记忆性还保留吗？如果 $Y$ 是一个与 $X$ 独立的指数分布，那么这个无记忆性依然保留。

### 泊松过程的差
显然，泊松过程的差不是泊松过程，而是复合泊松过程。
$$
\begin{align*}
G_{N(t)}(z)\\
&= \mathrm{E}(Z^{N_{1}}) \mathrm{E}(Z^{-N_{2}} )\\
&= G_{N_{1}}(z) G_{N_{2}}\left(\dfrac{1}{z}\right)\\
&= \exp\left((\lambda_{1} + \lambda_{2}) t \left(\dfrac{\lambda_{1}}{\lambda_{1} + \lambda_{2}}\right)z + \left(\dfrac{\lambda_{2}}{\lambda_{1} + \lambda_{2}}\right)z^{-1}\right) 
\end{align*}
$$
中间的部分是一个两点分布的母函数，以 $\dfrac{\lambda_{1}}{\lambda_{1}+ \lambda_{2}}$ 概率取 $+1$，这与我们的直观是相符合的。

再给一个小小的脑筋急转弯！
>[!QUESTION]
>三个人去银行，银行只有两个柜台。每个柜台对每个顾客的服务时间服从参数为 $\lambda$ 的指数分布。问一开始等待的那个人在银行中平均待了多久？
>
显然，等待时间是服从参数为 $2\lambda$ 的指数分布，而服务时间是服从参数为 $\lambda$ 的指数分布。因此，时间期望为 $\dfrac{3}{2\lambda}$。

>[!QUESTION]
>三个人去银行，银行只有两个柜台。两个柜台的服务效率分别为 $\lambda_{1},\lambda_{2}$。问一开始等待的那个人在银行中平均待了多久？

直观上：
$$
\dfrac{1}{\lambda_{1}+\lambda_{2}}  + \dfrac{1}{\lambda_{1}} \cdot \dfrac{\lambda_{1}}{\lambda_{1}+ \lambda_{2}} + \dfrac{1}{\lambda_{2}}\cdot \dfrac{\lambda_{2}}{\lambda_{1} + \lambda_{2}} = \dfrac{3}{\lambda_{1}+ \lambda_{2}}
$$
我们详细算一下后半部分：
$$
\begin{align*}
\mathrm{E}(T) &= \mathrm{E}(T|T_{1}>T_{2})P(T_{1}>T_{2}) + \mathrm{E}(T|T_{1}<T_{2})P(T_{1}<T_{2})\\
&= \dfrac{1}{\lambda_{2}} P(T_{1}>T_{2}) + \dfrac{1}{\lambda_{1}} P(T_{1}<T_{2})
\end{align*}
$$
我们详细计算一下其中的概率：
$$
\begin{align*}
P(T_{1}>T_{2})\\
&= \iint  f(t_{1},t_{2}) dt_{1}dt_{2}\\
&= \iint  \lambda_{1} \lambda_{2}\exp(- \lambda_{1}t_{1})\exp(- \lambda_{2} t_{2})dt_{1}dt_{2}\\
&= \dfrac{\lambda_{2}}{\lambda_{1} + \lambda_{2}}
\end{align*}
$$
从而验证了我们的直观想法是正确的。

### 一个引子
我们将泊松过程事件发生的时刻记为 $\lambda_{1},\lambda_{2},\cdots ,\lambda_{n}$，我们现在计算 $\mathrm{E}(S_{4}|N(1)=2)$。一个很容易想到（但可能不是那么容易实施）的计算方法是先计算 $F_{S_{4}}(t|N(1)=2)$：
$$
\begin{align*}
F_{S_{4}} (t|N(1)=2) \\
&=\dfrac{P(S_{4}\le t ,N(1)=2)}{P(N(1)=2)}\\
&= \dfrac{P(N(t)\ge 4,N(1)=2)}{P(N(1)=2)}\\
&= \dfrac{P(N(t)-N(1)\ge 2)P(N(1)=2)}{P(N(1)=2)}\\
&= P(N(t)-N(1)\ge 2)
\end{align*}
$$
然后继续计算即可。最终的答案是：
$$
\mathrm{E}(S_{4}|N(1)=2) = \dfrac{2}{\lambda} + 1
$$
然而这个答案似乎是可以被直观看出来的？真的吗？这并不是一个简单的事情！

