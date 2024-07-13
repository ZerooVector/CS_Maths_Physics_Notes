#StochasticProcess  

## Probability 
### 概率的连续性
为了说明概率的连续性，我们需要定义事件的 Increasing Sequence 和 Decreasing Sequence 。如果一个序列是 Increasing，那么
$$
E_{n} \subset E_{n+1} 
$$
也就是下一个事件总能包含上一个，Decreasing 定义与其相反。那么，我们定义一个 Increasing Seq 的极限为：
$$
\lim_{n \rightarrow \infty} E_{n} = \bigcup_{i}E_{i} 
$$
而一个 Decreasing Seq 的极限为：
$$
\lim_{n \rightarrow \infty} E_{n} = \bigcap_{i} E_{i} 
$$
那么，我们有：
##### Theorem
如果 $E_{n}$ 是上升序列或者下降序列，那么：
$$
\lim P(E_{n}) = P(\lim  E_{n})
$$
##### Proof
我们定义一些相互排斥的事件 $F_{i}$：
$$
F_{1}= E_{1}
$$
$$
F_{n} = E_{n}(\bigcup_{i}^{n-1}E_{i})^{c} = E_{n}(E_{n-1})^{c}
$$
那么我们容易注意到：
$$
\bigcup_{i=1}^{n} F_{i} = \bigcup_{i=1}^{n}  E_{i}
$$
那么
$$
\begin{align*}
P(\bigcup^{\infty} E_{i}) &= P(\bigcup^{\infty}  F_{i})\\
&= \lim_{n \rightarrow  \infty} \sum_{i}^{n}P(F_{i})\\
&= \lim_{n \rightarrow\infty }P(\bigcup^{n}F_{i})\\
 &= \lim_{n \rightarrow \infty} P(E_{i})
\end{align*}
$$
（主要证明方法：构造互斥序列 $F_{i}$，从而将括号里面的并集符号转换成括号外面的求和号，并且在外面取极限）
另外一边证明方式类似，不再赘述。

##### Lemma : Borel-Catelli Lemma 
对于一个序列 $E_{i}$，如果
$$
\sum_{i}^{\infty} P(E_{i}) < \infty 
$$
则记事件 $A$ 为：序列中无穷个事件发生，那么
$$
P(A)  = 0
$$
##### Proof
我们首先定义序列的上极限：
$$
\lim_{i \rightarrow \infty }\sup E_{i} = \bigcap_{n=1}^{\infty} \bigcup_{i=n}^{\infty}E_{i}
$$
那么，显然可以知道，如果有无穷个 $E_{i}$ 发生，那么序列的上极限必然发生。那么，由于 $\bigcap_{i=n}^{\infty}E_{i}$ 是一个递减的序列，我们将无数个递减的序列并起来，那么：
$$
\begin{align*}
P(\lim_{i \rightarrow \infty} \sup  E_{i})& = P(\lim_{n \rightarrow\infty} \bigcup_{i=1}^{n}E_{i})\\
 &= \lim_{n \rightarrow \infty }P(\bigcup_{i=1}^{n} E_{i})\\
&=0  
\end{align*}
$$ 
其中，最后一步就是 Cauchy 收敛准则

##### Converse to BC-Lemma 
如果 $E_{i}$ 是**独立事件**组成的序列，且
$$
\sum_{n-1}^{\infty}  P(E_{n}) = \infty 
$$
那么，事件 $A$： 序列中有无穷个事件 $E_{i}$ 发生的概率为 1.
##### Proof 
上面已经说过，由于序列的上极限是一系列递减事件的交，那么（注意：这里不能把事件的并的概率放缩成把所有事件的概率加起来，这样会导致一个小于号，然后方向就不对了）
$$
\begin{align*}
P(A) &= P(\lim_{n \rightarrow \infty}\bigcup_{i=n}^{\infty}E_{i})\\
&= \lim_{n \rightarrow \infty} P(\bigcup E_{i})\\
&= \lim_{n \rightarrow \infty} [1-P(\bigcap E_{i}^{c})] 
\end{align*}
$$
再注意到：
$$
\begin{align*}
P(\bigcap_{i}E_{i}^{c}) &= \prod_{i}P(E_{i}^{c})\\
 &= \prod_{i}(1-P(E_{i}))\\
&\le \exp(-\sum_{n}^{\infty}P(E_{i}))\\
&= 0\\ 
\end{align*}
$$
那么原问题得证。

## Random Variables 

## Mathmatical Expectations 
我们介绍一些可能有用的等式。使得 $A_{i}$ 代表事件，$I_{i}$ 是一系列的 Indicator Variables。定义：
$$
N = \sum_{i}I_{i}
$$
那么注意到：
$$
(1-1)^{N }= \sum_{i=0}^{N}C_{N}^{i} (-1)^{i} = \sum_{i=0}^{n}C_{N}^{i}(-1)^{i}
$$
定义 $I$，使得在 $N>0$ 时 $I>0$，否则 $I=0$。那么注意到：
$$
1-I = \sum_{i=0}^{n}C_{N}^{i}(-1)^{i}
$$
可以改写成：
$$
I = \sum_{i=1}^{n} C_{N}^{i} (-1)^{i+1} 
$$
（指数上的 $i+1$ 是从一个负号变过来的）
两边取期望：
$$
E[I] = E[N]-E[C_{N}^{2}]+\cdots +(-1)^{n+1}E[C_{N}^{n}]
$$
然后又可以注意到 $E[I]$ 的意义是 $A_{i}$ 中至少一个事件发生的概率，那么：
$$
E[I] = P(N>0) = P(\bigcup A_{i})
$$
那么你其实可以得到等式：
$$
P(\bigcup A_{i}) = \sum_{i}P(A_{i}) - \sum_{i<j} P(A_{i}A_{j}) +\sum_{i<j<k} P(A_{i}A_{j}A_{k}) \cdots +(-1)^{n+1} P(A_{1}A_{2}\cdots A_{n})
$$

其他公式也可以使用类似的方式导出。例如，我们想要求解恰好只有 $r$ 个事件出现的概率，只要定义 indicator variable :
$$
C_{N}^{r}(1-1)^{N-r} = I_{r}
$$

==需要补充== 

## Moment Generating, Characteristic Functions, and Laplace Transforms 

随机变量 $X$ 的矩母函数 (Moment Generating Function)定义为：
$$
\psi (t) = \int e^{tx}dF(x) = \int e^{tx}f(x)dx = E[e^{tX} ]
$$
它首要的作用是方便地求解 $X$ 的各阶矩：
$$
\psi^{(n)} (t) = E[X^{n}e^{tX}]
$$
接下来计算 $t=0$ 时的值即可。显然，这个积分可能不收敛，矩母函数未必存在。因此我们定义特征函数 (Characteristic Function)
$$
\phi (t) = E[e^{itX}]
$$
显然，我们是可以定义联合分布的矩母函数和特征函数。此外，我们定义随机变量的 Laplace 变换为：
$$
\tilde F(s) = \int_{0}^{\infty}e^{-sx}dF(x)
$$
其中 $s=a+bi$。

我们可以定义多个变量的联合矩母函数为：
$$
\psi (t) = E[\exp (\sum_{i}t_{i}X_{i})]
$$
这样，它对 $t$ 求导之后，得到的是多个随机变量的和的分布。

## Conditional Expectation
在 $Y=y$ 给定时，$X$ 的条件分布显然为：
$$
P(X\le x|Y=y) = \frac{P(X\le x,Y=y)}{P(Y=y)}
$$
那么
$$
E[X|Y=y] = \int x\ dF(x|Y=y)
$$
条件期望的一个性质是：
$$
E[X] = E[E[X|Y]] = \sum E[X|Y=y] P(Y = y)  = \int E[X|Y=y]  dF(y)
$$
因此，$E[X]$ 也可以看作一个加权平均值，它对不同的 $Y=y$ 时，$X$ 的期望进行加权。

### 条件期望和 Bayes 估计
在 Bayes 估计中，我们通常是要基于数据 $X$ 的值，使用一个函数 $d(X)$ 来估计未见的 $\theta$ 的值。使得 $E[(d(X)-\theta )^{2}|X]$
最小化。由于在 $X$ 取定时，$d(X)$ 是一个常数，那么这个估计显然是：
$$
d(X) = E[\theta |X]
$$
也就是说，我们将依赖于在观测值 $X$ 下，$\theta$ 的期望进行估计。
如果估计结果满足（这里为什么要将 $\theta$ 作为条件？）
$$
E[d(X)|\theta ] = \theta 
$$
我们称这个估计是无偏的。那么下面我们来说明贝叶斯估计在什么时候是无偏的。

##### Lemma 
首先我们证明：对于任意随机变量 $Y$ 和随机向量 $Z$，有：
$$
E[(Y-E[Y|Z])E[Y|Z]] = 0
$$
利用上文中提到的条件期望的性质（多一层期望，就可以多对一个变量取条件，这是一种将新的变量拿进期望计算式的方法），有：
$$
E[YE[Y|Z]] = E[E[YE[Y|Z]|Z]]  = E[E[Y|Z]E[Y|Z]]
$$
这是由于对每一个确定的 $Z$，$Y$ 的值都是常数，因此可以将 $E[Y|Z]$ 拿出来

##### Theorem :  Bayes 估计只有在点估计的情况下才是无偏的
在上面的引理中，令随机变量 $Y$ 为我们要估计的未定量 $\theta$，随机向量 $Z$ 为我们的一系列数据 $X$，那么我们有：
$$
E[\ (\theta -E[\ \theta \ |X\ ]\ )\ E[\ \theta |X\ ]\ ] = 0
$$
令 $Y = E[\theta |X] = \theta$，根据上面的定义，这说明 $Y$ 是 Bayes 估计量，并且是一个无偏估计。代入上式，我们就得到：
$$
E[(E[\theta |X] - \theta ) \theta  ]= 0
$$
将上面两式相加（这个构造太技巧化）：
$$
E[(\theta-E[\theta|X])E[\theta|X]] +E[(E[\theta |X] - \theta ) \theta  ] = 0
$$
把期望算符移动到最外层：
$$
E[(\theta-E[\theta|X])E[\theta|X]+(E[\theta |X] - \theta ) \theta ] = 0
$$
那么我们可以推出
$$

$$





## Exponential Distribution, Lack of Memory, and Hazard Rate Functions
指数分布的矩母函数为:
$$
E[e^{tX}] = \frac{\lambda}{\lambda-t }
$$
我们说指数分别是无记忆性的，那么：
$$
P[X>s+t|X>t] = P[X>s]
$$
或者，我们换个说法：记
$$
\bar F(x) = P(X \ge x)
$$
那么
$$
\bar F(s+t) = \bar F(s) \bar F(t)
$$
指数分布的失效率函数被记为：
$$
\lambda(t) = \frac{f(t)}{\bar F(t)}
$$
意义是在单位时间内失效的零件占目前所剩零件的比例。

## Some Probability Inequalities 
##### Lemma : Markov's Inequality
对于 $a>0$，
$$
P[X \ge a] \le \frac{E[X]}{a}
$$
这个容易证明，定义 Indicator Variable $I(x \ge a)$，写出：
$$
aI(x \ge a) \le X
$$
两边取期望即可

##### Theorem : Chernoff Bounds 
$$
P(X \ge a) \le e^{-ta}M(t)
$$
这个容易证明：
$$
P(X \ge a) = P(e^{tX} \ge e^{ta}) \le E(e^{tX})e^{-ta} 
$$

##### Theorem : Jensen's Inequality 
如果 $f$ 是 Convex function，那么：
$$
E[f(X)] \ge f(E[X])
$$

## Limit Theorems 
##### Strong Law of Large Numbers 
如果 $X_{i}$ 是 iid 的均值为 $\mu$ 的变量，那么
$$
P\left(\lim_{n \rightarrow \infty} \frac{1}{n}\sum_{i}X_{i} = \mu \right)=1
$$
##### Central Limit Theorem








