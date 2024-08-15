#StochasticProcess 

另外一种采样的方法是构建一个马氏链，使得其平稳分布恰好是我们想要的。假设我们想要分布 $\pi$，马氏链的转移矩阵是 $P$，那么必然有 $\pi P = \pi$。对于 $n$ 个状态的马氏链，$n^{2}$ 个未知数却只有 $n$ 个方程，不够！因此需要补充精细平衡条件 $\pi_{i}p_{ij} = \pi_{j}p_{ji}$ ，它比 $\pi P = \pi$ 更强。Metropolis 算法是 MCMC 算法的一种：
- 提案阶段：提出一个想要转移到的的新分布
- 决策阶段：决定是否要转移到这个新分布 
因此，转移矩阵一般长成下面这个样子：
$$
p_{ij} = \begin{cases}
Q_{ij}A_{ij} \quad  i \not = j  \\
1 - \sum_{i \not = j }p_{ij} \quad i = j 
\end{cases}
$$
这里我们将 $Q$ 称为提案矩阵，而 $A$ 称为决策矩阵。我们这里要求 $Q$ 是对称的，那么，假如我们要采样的是 Gibbs 分布，精细平衡条件就是：
$$
\dfrac{p_{ij}}{p_{ji}} = \dfrac{A_{ij}}{A_{ij}} =  \dfrac{\pi_{j}}{\pi_{i}} = \exp( - \beta \Delta H_{ij})
$$
有两种使得 $A$ 满足精细平衡条件的选法：
- $A_{ij} = \min(1,\exp(- \beta \Delta H_{ij}))$
- $A_{ij} = (1+\exp(\beta \Delta H_{ij}))^{-1}$

而 $Q$ 矩阵的选择与系统的性质有关。例如这里考虑一个一维的伊辛模型，每个粒子的自旋方向只能是向上 （+1）或者向下（-1）, 系统的哈密顿量是：
$$
J(x) = - J \sum_{|i - j |  =1} x_{i} x_{j} - h \sum_{i} x_{i}
$$
系统的磁化强度是 $M_{a}(x) = \sum x_{i}$，而平均磁化强度是 $m (x)  = \dfrac{M_{a}(x)}{m}$。我们希望求解：
$$
m = \sum_{x}m(x) \dfrac{\exp( - \beta H(x))}{Z_{M }}
$$
我们要使用时间平均来代替系综平均。那么 $Q$ 矩阵有两种常见的设置方法（注意：$Q$ 矩阵无论怎么设置，$A$ 矩阵已经保证我们的设置满足了精细平衡条件）：
等概率的方法：
$$
Q(x \rightarrow y) = \begin{cases}
\dfrac{1}{N_{t}-1} \quad x \not = y  \\
0 \quad x = y
\end{cases}
$$
吉布斯采样算法：
$$
Q(x \rightarrow  y) = \begin{cases}
\dfrac{1}{M} \quad x \not = y \ \text{only at one site} \\
0 \quad  \text{otherwise}
\end{cases}
$$
实际上，关于 $Q$ 的对称要求可以被放松，只需要 $A$ 和 $Q$ 之间满足关系：
$$
A_{ij} = \min\left( 1 , \dfrac{Q_{ji}\pi_{j}}{Q_{ij}\pi_{i}}\right)
$$
接下来再介绍该算法在贝叶斯统计中的应用。在一般的统计推断中，我们通常要极大化似然函数：
$$
L(\theta|X) = \prod_{i} p(X_{i} | \theta)
$$
来确定参数。但是，在贝叶斯统计中，$\theta$ 也被认为是一个具有分布 $\mu(\theta)$ 的随机变量，换言之，我们相信对于 $\theta$ 的先验知识可以帮助我们建立更好的模型。$\theta$ 的后验分布是：
$$
\pi(\theta |X) = \dfrac{L(\theta|X) \mu(\theta)}{\int L(\theta|X) \mu(\theta) d \theta} = \dfrac{1}{Z} L(\theta|X) \mu(\theta)
$$
我们可以使用 Metropolis 算法计算 $\theta$ 的均值，这不要求我们事先知道 $Z$ 的值。

