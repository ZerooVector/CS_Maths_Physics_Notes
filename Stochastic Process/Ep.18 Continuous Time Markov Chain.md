#StochasticProcess 

我们谈一谈连续马尔可夫链。此时，转移的步数被转移的时间所取代了：
$$
P_{ij}(t) = P(X(t)=j|X(0)=i)
$$
那么，我们需要稍微改写 CK 方程，只是把转移步数换成了时间而已：
$$
P_{ij}(t+s) = \sum_{k}P_{ik}(s)P_{kj}(t)
$$
从而，利用矩阵乘法，CK 方程仍然写成：
$$
P(t+s) = P(t)P(s)
$$
对于离散时间马尔科夫链，我们可以把它拆解到一步转移概率。但是，我们现在不行了。我们现在要回答的最重要的问题是：连续时间马尔科夫链的基本转移行为是什么？
我们考虑：
$$
\lim_{t \rightarrow 0}P(t) \rightarrow I 
$$
我们之前做了一个递推方程（差分方程），现在，我们希望做一个微分方程。考虑：
$$
\begin{align*}
\lim_{\Delta t \rightarrow 0 }\dfrac{P(t+\Delta t) - P(t) }{\Delta t} &= \lim_{\Delta t \rightarrow 0 }\dfrac{P(t)(P(\Delta t)-I)}{\Delta t}\\
&= P(t) \lim_{\Delta t \rightarrow 0 }\dfrac{1}{\Delta t}(P(\Delta  t)-I)\\
&= P(t)Q
\end{align*}
$$
我们将这里的矩阵 $Q$ 称为**生成元**（Generator）。
那么，微分方程
$$
\dfrac{\mathrm{d}}{\mathrm{d}t}P(t) = P(t)\cdot Q \quad P(0) = I
$$
的解是：
$$
P(t) = \exp(Qt)
$$
我们将上面的方程称为**前进方程**。此外，我们可以列出解完全相同的**后退方程**。
$$
\dfrac{\mathrm{d}}{\mathrm{d}t} P(t)= Q\cdot P(t)
$$
我们来研究一下 $Q$ 矩阵的特点。我们知道，对于离散的情况，我们有：
$$
P_{ij}(t) \ge 0 \quad \sum_{j}P_{ij}(t) = 1
$$
而现在，$Q$ 的值在非对角元上是 $\ge 0$ 的，而在对角元上是 $\le 0$ 的。显然，$Q$ 矩阵的行和是 0.

>[!EXAMPLE]
>我们希望计算泊松过程的 $Q$ 矩阵。

注意到：
$$
\begin{align*}
P_{ij}(t) &= P(N(t)=j-i) \\
&= \dfrac{(\lambda t)^{j-i}}{(j-i)!} \exp(- \lambda t) \quad (j>i)
\end{align*}
$$
我们现在对 $Q$ 矩阵中的元素各个击破，先计算对角线元：
$$
\begin{align*}
\lim_{\Delta t \rightarrow 0} \dfrac{1}{\Delta t} (P_{ii}(\Delta t)-1) \\
&= \lim_{\Delta t \rightarrow 0} \dfrac{1}{\Delta t} (\exp(-\lambda\Delta t)-1)\\
&= - \lambda
\end{align*}
$$
非对角线元：
$$
\lim_{\Delta t \rightarrow 0} \dfrac{1}{\Delta t} \dfrac{(\lambda\Delta t)^{j-i}}{(j-i)!} \exp(- \lambda \Delta t ) = \begin{cases}
\lambda \quad j = i+1  \\
0 \quad j\ge i+2 
\end{cases}
$$
因此，它的生成元长成这个样子：
![[Pasted image 20240224233640.png|350]]

我们今天不展开连续时间马氏链的基本性质。只展示几个基本的性质。我们直接来考虑其极限行为 $P_{ij}(t) \rightarrow ?$。在离散链里面，就算极限分布不存在，我们的稳态分布也在刻画转移到某个状态的次数与总转移次数的比例。现在，我们的连续链中，从一个态转移到另一个态需要历经两个步骤：停留和跳转。我们现在将稳态概率 $P_{j}$ 定义成在态 $j$ 上停留的时间和总时间的比例。（$P_{j}$ 与初值无关需要不可约的条件）
此外，连续时间没有“周期性”的定义。在连续时间的情况下，假如 $\exists t_{0} ,P_{ij}(t_{0})>0$，则 $\forall t,P_{ij}(t)>0$。直观上，$P_{ij}(t_{0})>0$ 意味着状态 $i$ 和状态 $j$ 是“连通”的，只不过我们这次跳转的过程中，停留时间为 $t_{0}$，因此对于任意停留时间都可以从 $i$ 跳转到 $j$。因此，我们有一个直观：**对于连续时间马氏链来说，如何跳转、哪些状态之间能跳转已经由生成元规定好了，这些跳转的“通路”不会断掉。只是在每个态上，我们需要停留一定的时间，这个停留的时间是（服从指数分布的）随机变量，时间越长，在一个态上停留的概率越低，这导致了转移概率随着时间的变化。** 在离散时间马氏链中，我们要求“非周期”只是为了避免某种直观上的“震荡”，而在连续链中，这种“震荡”不会出现，因此连续链只要“不可约”，就有极限分布。

我们现在开始计算这个极限分布。显然，我们要利用柯尔莫哥洛夫方程：
$$
\dfrac{\mathrm{d}}{\mathrm{d}t} P(t) = P(t) \cdot Q  = Q \cdot P(t)
$$
在时间足够长时，$P(t)$ 不再变化。我们使用第二个方程得到：
$$
0 = \pi Q
$$
$\pi$ 依然是个行向量。

我们举个例子看看。
>[!EXAMPLE] M/M/1 排队模型
>此时，顾客按照泊松过程来，按照泊松过程走。顾客的等待时间中包含纯等待时间，各个顾客的纯等待时间是不独立的，因此我们无法使用过滤泊松模型处理。现在，我们要使用**生灭过程**来处理这个问题。

生灭模型实质上是一种连续时间马尔科夫链。我们假设现在的状态表示了一个种群的数量，种群数量由生和灭两种机制控制。种群在短时间内出生 1 人的概率是时间的线性函数，出生 2 人的概率是时间的高阶无穷小；在短时间内死亡 1 人的概率也是时间的线性函数，死亡 2 人以上的概率也是时间的高阶无穷小。
我们可以将泊松过程称为纯生过程。

我们开始计算：
$$
P_{ii}(\Delta t) = (1 - \lambda_{i}\Delta t )(1- \mu_{i}\Delta t ) + \lambda_{i}\Delta   t \cdot \mu_{i}\Delta t  = 1-(\lambda_{i}+\mu _{i})\Delta t
$$
（这里我个人写的时候已经略去了很多高阶项，不严谨）
$$
P_{i,i+1}(\Delta t) = \lambda_{i}\Delta t  (1 - \mu_{i}\Delta t) + \cdots  = \lambda_{i}\Delta t 
$$
$$
P_{i,i-1} (\Delta t)=  (1- \lambda_{i}\Delta t) (\mu _{i}\Delta t) = \mu_{i}\Delta t 
$$
$$
P_{i,j}(\Delta t) = o(t) \quad |i-j|\ge 2
$$
因此，我们成功计算了 $\Delta t$ 时间的转移矩阵（这样做的目的是我们可以给出“线性”这样的假设，而且后面算 $Q$ 矩阵的时候总是要求导的）。我们现在要根据定义算出 $Q$ 矩阵。
$$
Q_{ii} = - (\lambda_{i}+\mu_{i}) \quad Q_{i,i+1} = \lambda_{i}\quad Q_{i,i-1} =\mu_{i} \quad Q_{\text{others}} = 0 
$$
其中，特殊边界值：$Q_{00} = -\lambda_{i}$。
因此，这里的 $Q$ 矩阵是一个三对角矩阵：
![[Pasted image 20240225004649.png|500]]
最后，我们来计算稳态分布：
$$
\pi Q = 0
$$
从而：
$$
\begin{align*}
\pi_{0}\lambda_{0}+ \pi_{1}\mu_{1} &= 0 \\
\pi_{0}\lambda_{0}- \pi_{1}(\lambda_{1}+\mu_{1}) + \pi_{2}\mu_{2} &= 0 \\
\cdots \\
\pi_{k-1}\lambda_{k-1}- \pi_{k}(\lambda_{k}+\mu_{k}) + \pi_{k+1} \mu_{k+1} &= 0 
\end{align*}
$$
注；这里我补一点自己的直观。$Q$ 矩阵的对角元意味着“离开 $i$ 态的速度“”，非对角元意味着“从 $i$ 态进入 $j$ 态的速度”（这由离开 $i$ 态的速度和从 $i$ 态转向 $j$ 态的概率共同决定），这样的直观呼应了前面的连续马氏链转移的两个过程，也可以看出为何 $Q$ 的行和为 0。
解以上方程式（不断将上面的式子向下代入即可）得到：
$$
\pi_{k}= \dfrac{\prod_{i=0}^{k-1} \lambda_{i}}{\prod_{i=1}^{k} \mu_{i}} \pi_{0} \quad \pi_{0} = \left(1+\sum_{n=1}^{\infty} \sum_{k=1}^{n} \dfrac{\lambda_{k-1}}{\mu_{k}}\right) ^{-1} 
$$
至此，我们求出了生灭模型的极限分布。

我们现在使用生灭过程描述 M/M/1 排队系统。根据泊松过程的性质，我们有：
- $\Delta t$ 内进入一人的概率为 $\lambda \Delta t +o(t)$
- 进入两人及以上的概率为高阶项
-  $\Delta t$ 内离开一人的概率为 $\mu \Delta t +o(t)$
- 离开两人及以上的概率为高阶项
显然，我们只要取 $\lambda_{i} = \lambda,\mu_{i} = \mu$，那么我们得到：
$$
\pi_{0} = \dfrac{1}{\left(1+ \sum_{n=1}^{\infty} \left(\dfrac{\lambda}{\mu }\right)^{n}\right)} = \dfrac{\mu  - \lambda}{\mu }
$$
显然，级数的收敛条件是 $\lambda<\mu$，也就是“来得比去得慢”，否则，你的队伍就会越来越长，此时我们也无法求出稳态分布（$\lambda>\mu$ 时所有状态都不是常返态）。
我们继续计算：
$$
\pi_{n} = \dfrac{\mu  - \lambda}{\mu } \left(\dfrac{\lambda}{\mu }\right)^{n}
$$
我们计算平均队长：
$$
\bar L = \sum_{n} \dfrac{\mu  - \lambda}{\mu } \left(\dfrac{\lambda}{\mu }\right)^{n} \cdot n = \dfrac{\lambda}{\mu  - \lambda}
$$
我们再计算每个人的平均等待时间，这个时间是前面所有人（平均队长，注意这个队长不包括自己）的服务时间+自己的服务时间：
$$
\dfrac{\lambda}{\mu  - \lambda }\dfrac{1}{\mu } + \dfrac{1}{\mu } = \dfrac{1}{\mu  - \lambda }
$$
因此，我们得到了排队论中重要的结论：
$$
\bar L = \lambda \bar T
$$
其中，$\bar L$ 为平均队长，$\bar T$ 为平均等待时间，它可以推广到更多的排队模型。它被称为“Little 公式”。








