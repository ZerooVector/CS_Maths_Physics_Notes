#StochasticProcess  
**这里梳理随机过程第二章的所有重点定理** 

## Poisson 过程的几个定义
##### 计数过程
计数过程：若随机变量 $N(t)$ 表示直至时刻 $t$ 已经发生的事件的总数，那么随机过程 $\{N(t), t\ge 0\}$ 称为计数过程。一个计数过程要满足如下条件：
- $N (t) \ge 0$
- $N(t)$ 为整数值
- $s<t$，则 $N (s) \le N(t)$
- $s<t$，则 $N (t) - N(s)$ 代表发生在 $(s,t]$ 中的事件数

##### Poisson 过程：一类特殊的计数过程
如果一个计数过程又满足了如下条件, 那么它就被称为是一个 Possion 过程：
- $N (0) = 0$
- 独立增量
- 泊松分布

一个 Poisson 过程还有着如下的定义：
- $N (0) = 0$
- 平稳增量和独立增量
- $P (N (h) = 1) = \lambda h +o(h)$
- $P (N (h) = 2) = o(h)$
这意味着，在微元时间 $h$ 之内，Poisson 过程中的事件发生速率为 $\lambda$，事件的发生次数正比于 $h$

##### 到达时间间隔的分布
- Poisson 过程中任意两个事件的时间间隔服从指数分布
- 第 $n$ 个事件的等待时间具有以 $n$ 和 $\lambda$ 为参数的 Gamma 分布（这在第一章作业中已经证明过）

## 到达时间的条件分布
##### 到达时间和均与分布的关系
- 如果在一段长为 $t$ 的时间内发生了 1 个事件，那么这个事件发生在区间上哪一点的概率都是相同的，也就是说
$$
P(X_{1}<s |N(t) = 1) = \frac{s}{t}
$$
- 若已知在 $(0,t)$ 内已经发生了 $n$ 个事件，那么这些事件的到达时间就与 $n$ 个在 $[0,t]$ 上均匀分布的随机变量的次序统计量有相同的分布。这是对上面结论的自然推广，因为每一个事件的到达时间都是均匀分布的随机变量

##### 分类的事件
- 如果一个事件发生在时刻 $s$，被分为 I 类事件的概率为 $P(s)$，那么我们记：
$$
p = \frac{1}{t} \int_{0}^{t} P(s)ds 
$$
那么 I 型事件和 II 型事件到达的过程实际上服从参数为 $\lambda p$ 和 $(1-\lambda) p$ 的 Possion 分布

##### 使用均匀随机变量控制其他随机变量
若 $Y_{1}, Y_{2},\cdots ,Y_{n}$ 是 iid 的非负随机变量，那么：
$$
E[Y_{1}+Y_{2}+\cdots +Y_{k} | Y_{1}+Y_{2}+\cdots +Y_{n} = y] = \frac{k}{n} y
$$
这是符合直觉的。

现在，找到 $n$ 个在 $(0,t)$ 上均匀分布的随机变量按照次序的值 $\tau_{1},\tau_{2}\, \cdots ,\tau_{n}$，令 $Y_{1}, Y_{2},\cdots ,Y_{n}$ 是 iid 的随机变量，并且要和 $\tau_{i}$ 独立。那么：
$$
P(Y_{1}+\cdots +Y_{k} < \tau_{k} ,k=1,2,\cdots ,n |Y_{1}+Y_{2}+\cdots +Y_{n} = y) = \mathrm{clip}(1- \frac{y}{t},0,1)
$$
这个定理反映了一组均匀随机变量控制另外一组 iid 随机变量的能力。在已知 $Y_{1}+\cdots +Y_{n}= y$ 的情况下，$k$ 个 $Y_{i}$ 的和小于 $\tau_{k}$，对于所有 $k$ 均成立的可能性就可以被看作是 $\tau_{i}$ 控制 $Y_{k}$ 的能力。在这些 $Y_{i}$ 的和超过 $t$ 时，显然 $\tau_{i}$ 就不能控制 $\tau_{i}$ 了

## 非时齐的 Poisson 过程
如果强度函数是可变的 $\lambda(t)$，那么这样的过程就是非时齐的 Poisson 过程。令一个时间段上的平均到达量为：
$$
m(t) = \int_{0}^{t} \lambda(s)ds 
$$
那么，在 $(0,t)$ 上的总到达数就服从以 $m(t)$ 为参数的 Poisson 分布。

此外，非时齐 Possion 过程可以看作是从一般的 Possion 过程上的采样。只要让到达速率的 $\lambda$ 的一般 Possion 过程上的事件有 $\lambda (t) / \lambda$ 的概率被计数，那么我们就得到了一个非时齐的 Possion 过程。

## 复合 Possion 过程
令 $X_{1}, X_{2},\cdots$ 是 iid 的有分布函数 $F$ 的随机变量序列，且这个序列与一个均值为 $\lambda$ 的随机变量 $N$ 独立。随机变量
$$
W = \sum_{i=1}^{N} X_{i}
$$
称为具有参数 $\lambda$ 和分布 $F$ 的复合 Possion 随机变量。说白了，就是将数量服从 Poisson 分布的随机变量加起来。那么它的期望和方差服从如下结论：
$$
\mathrm{E}[W] = \lambda \mathrm{E}[X] \quad  \mathrm{Var}(W) = \lambda \mathrm{Var}(W)
$$
关于复合泊松过程，我们有一个恒等式：若取 $W$ 为一个复合泊松随机变量，$X$ 为一个与 $W$ 独立的随机变量，那么：
$$
\mathrm{E}[Wh(W)] = \lambda \mathrm{E}[Xh(W+X)]
$$
这个恒等式的最大作用是计算 $W^n$ 的期望：
$$
\mathrm{E}[W^{n}] = \lambda \sum_{j=0}^{n-1} E[W^{j}]E[X^{n-j}]
$$
如果有一个 Poisson 过程 $N(t)$，那么：
$$
X(t) = \sum_{i=1}^{N(t)} X_{i}
$$
就是一个复合 Poisson 过程。例如，进入花店的顾客是泊松流，而每位顾客花的钱数是 iid 的随机变量，那么在时间 $t$ 之前，所有顾客花掉的钱数就是复合 Poisson 过程。

## 条件 Poisson 过程
条件 Poisson 过程是说 Poisson 过程的参数受到某个隐变量 $\Lambda$ 的控制，只有当 $\Lambda = \lambda$ 时，这个过程才是 Poisson 过程。最重要的是，我们通过观测时刻 $t$ 时发生了多少次事件，我们就可以推断  $\Lambda$ 的分布。这是因为：
$$
P(\Lambda \in (\lambda.\lambda+d \lambda )|N(t) = n) = \frac{P(\Lambda \in (\lambda.\lambda+d \lambda )|N(t) = n)P(N(t) = n)}{P(N(t) = n)} = \frac{e^{-\lambda t}\frac{(\lambda t)^{n}}{n!}dG(\lambda)}{\int_{0}^{\infty} e^{-\lambda t}\frac{(\lambda t)^{n}}{n!}dG(\lambda)}
$$

