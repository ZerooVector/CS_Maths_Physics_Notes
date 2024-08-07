## Chapter 10 Poisson 逼近
设 $X_{1}, X_{2},\cdots ,X_{n}$ 是具有：
$$
P(X_{i}=1) = \lambda_{i} = 1-P(X_{i}= 0)
$$
的伯努利随机变量，令 $W = \sum_{i=1}^{n}X_{i}$，Poisson 范例说明，若 $\lambda_{i}$ 都很小，且若 $X_{i}$ 都是独立的或者至多是“弱”相依的随机变量，则 $W$ 的分布讲近似于具有均值 $\lambda = \sum \lambda_{i}$ 的 Poisson 分布，从而
$$
P(W = k) = e^{-\lambda}\lambda^{k}/k!
$$
在 10.1 节中，我们介绍一种方法，它被称为 Brun 筛法的结果，建立在前面的近似有效性。在 10.2 节中，我们讲给出对于 Poisson 逼近的误差上界的 Stein-Chen 方法。在 10.3 节中，我们讲考虑对 $P(W=k)$ 的另一种逼近，它常常是上面确定的逼近的改进。

### 10.1 Brun 筛法
Poisson 逼近的有效性,，常常可用下述称为 Brun 筛法的结果建立：
命题 10.1.1 ：令 $W$ 为有界的飞赴整数值随机变量，若对一切 $i \ge 0$ 有：
$$
E[C_{W}^{i}] \approx \lambda^{i}/i!
$$
则
$$
P(W=j) = e^{-\lambda}\lambda^{j}/j!
$$
证明：令 $I_{j}(j \ge 0)$ 定义为：
$$
I_{j}= 
\begin{cases}
1 \quad W=j  \\
0 \quad others
\end{cases}
$$
于是，在 $r<0$ 或 $K>r$ 时可将 $C_{r}^{k}$ 理解为等于 0 后，我们有：
$$
I_{j}C_{W}^{j}(1-1)^{w-j} = C_{W}^{j} \sum_{k=0}^{W-j} C_{W-j}^{k}(-1)^{k}  = \sum_{k=0}^{\infty}C_{W}^{j} C_{W-j}^{k} (-1)^{k} = \sum_{k=0}^{\infty} C_{W}^{j+k} C_{j+k}^{k}(-1)^{k}
$$
取期望给出：
$$
P(W=j) = \sum_{k=0}^{\infty} E[C_{W}^{j+k}]C_{j+k}^{k}(-1)^{k} \approx \sum_{k=0}^{\infty}\frac{\lambda^{j+k}}{(j+k)!}C_{j+k}^{k}(-1)^{k} = \frac{\lambda^{j}}{j!}\sum_{k=0}^{\infty}(-\lambda)^{k} \frac{}{k!}= e^{-\lambda}\lambda^{j}/j!
$$

例子 10.1（A）设 $W$ 是参数为 $n,p$ 的二项分布遍历，其中 $n$ 很大，$p$ 很小，令 $\lambda = np$，并将 $W$ 解释为 $n$ 次独立重复实验中的成功次数，其中每次成功的概率为 $p$，故 $C_{W}^{i}$ 表示有 $i$ 次成功的集合数。现在，对这 $i$ 次实验的 $C_{n}^{i}$ 个集合中的每个，定义一个示性随机变量 $X_{j}$，若所有试验都成功，它等于 1，否则等于 0，那么：
$$
C_{W}^{j} = \sum_{j}X_{j}
$$
于是
$$
E[C_{W}^{i}] = C_{n}^{i}p^{i} = \frac{n(n-1)\cdots (n-i+1)}{i!}p^{i}
$$
因此，若 $i$ 相对于 $n$ 很小，则有：
$$
E[C_{W}^{i}] = \lambda^{i}/i!
$$
若 $i$ 相对于 $n$ 不是很小，那么 $E[C_{W}^{i}] \approx 0 \approx \lambda^{i}/i!$，故而我们得到对二项分布的经典 Poisson 逼近

例子 10.1（B）我们重新研究在例子 1.3（A）中考虑过的匹配问题，在此问题中，$n$ 个人将他们的帽子混合后每人随机取一个，以 $W$ 记取得了自己帽子的集合数，对 $i$ 个人的 $C_{n}^{i}$ 个集合的每个，定义一个示性随机变量：若此集合中的所有人都取得自己的帽子，那么它等于 1，否则等于 0. 则若 $X_{j}(j=1,2,\cdots ,C_{n}^{i})$ 是第 $i$ 个人的第 $j$ 个集合的示性函数，我们有：
$$
C_{W}^{i} = \sum_{j}X_{j}
$$
故而，对 $i \le n$，
$$
E[C_{W}^{i}] = C_{n}^{i} \frac{1}{n(n-1)\cdots (n-i+1)}=1/i!
$$
于是由 Brun 筛法，匹配数近似具有均值为 1 的 Poisson 分布。

例子 10.1（C）：考虑一些独立的实验，其中每个实验等可能地出现 $r$ 个可能结果之一，这里 $r$ 很大。以 $X$ 记直至至少其中一个结果已出现 $k$ 次时所需的试验次数，我们要用 Poisson 逼近来得到 $X$ 大于 $n$ 的近似概率。
以 $W$ 记在前 $n$ 次实验中至少已出现 $k$ 次的结果数，则：
$$
P(X>n) = P(W=0)
$$
假定在前 $n$ 次实验中任意指定的结果至少已出现 $k$ 次的可能性较小，我们现在论证 $W$ 的分布近似是 Poisson 分布。
作为开始，注意 $C_{W}^{i}$ 等于在前 $n$ 次实验中已出现 $k$ 次或者更多次的 $i$ 个结果的集合数，在对 $C_{r}^{i}$ 个集合的每个定义示性随机变量后，我们可见：
$$
E[C_{w}^{i}] = C_{r}^{i}p
$$
其中 $p$ 是在前 $n$ 次实验中指定的 $i$ 个结果已出现 $k$ 次或者更多次的概率。现在，每次试验导致 $i$ 个指定的结果中任一个出现的概率为 $i/r$，故而若 $i/r$ 很小，则由二项分布的 Poisson 逼近推出，在前 $n$ 次实验中出现 $i$ 个指定结果中的任一个的次数 $Y$ 近似地具有均值为 $ni/r$ 的 Poisson 分布。考虑出现 $i$ 个指定结果中的任意一个的 $Y$ 次实验，按哪 $i$ 个指定结果出现分类。若 $Y_i$ 是这 $i$ 个指定结果中的第 $i$ 个出现的次数，则由例子 1.5（I）推出 $Y_{j}$ 是独立的 Poisson 随机变量，每个具有均值 $\frac{1}{i}(ni/r)=n/r$，所以，我们由 $Y_{j}$ 的独立性可见 $p \approx (\alpha_{n})^{i}$，其中：
$$
\alpha_{n} = 1- \sum_{j=0}^{k-1}e^\frac{-n}{r}(n/r)^{j}/j!
$$
于是在 $i/r$ 很小时：
$$
E[C_{W}^{i}]\approx C_{r}^{i}\alpha_{n}^{i} \approx (r\alpha_{n})^{i}/i! 
$$
因此，在所有的情形下我们可见：
$$
E[C_{W}^{i}] \approx (r \alpha_{n})^{i}/i!
$$
所以，$W$ 是近似地是均值为 $r \alpha_{n}$ 的 Poisson 随机变量，故而：
$$
P(X>n) = P(W=0) \approx \exp(-r \alpha_{n})
$$
作为上式的一个应用，考虑生日问题：其中我们感兴趣的是直至至少有 3 个人是同一天过生日所需的人数。事实上这是上面在 $r = 365,k=3$ 的情形。于是
$$
P(X>n) = \exp(-365 \alpha_n)
$$
其中 $\alpha_{n}$ 是均值为 $n/365$ 的 Poisson 随机变量至少是 3 的概率。例如，对 $n=88,\alpha_{88}= 0.001952$，故而
$$
P(X>88) \approx \exp(-365\alpha_{n}) \approx 0.490
$$
即对房间中 88 个人近似以 51%的可能至少有三个人具有相同的生日。

### 10.2 给出 Poisson 逼近的误差界的 Stein-Chen 方法
如上一节，令 $W = \sum_{i=1}^{n}X_{i}$，其中 $X_{i}$ 是分别具有均值 $\lambda_{i}(i=1,2,\cdots ,n)$ 的伯努利随机变量。令 $\lambda = \sum_{i=1}^{n}\lambda_{i}$，并以 $A$ 记非负整数的一个集合。在本节中我们介绍在用 $\sum_{i \in A}e^{-\lambda}\lambda^{i}/i!$ 近似 $P(W \in A)$ 时确定误差上界的方法，称之为 Stein-Chen 方法。
作为开始，对固定的 $\lambda$ 和 $A$，我们定义一个函数 $g$ 使得：
$$
E[\lambda g(W+1) - Wg(W)] = P(W \in A)- \sum_{i \in A}e^{-\lambda} \lambda^{i}/i!
$$
这可归纳地完成如下：
$$
g(0) = 0
$$ 
而对 $j \ge 0$ 定义
$$
g(j+1) = \frac{1}{\lambda} [I(j \in A) - \sum_{i \in A}e^{- \lambda}\lambda^{i}/i!+jg(j)]
$$
其中 $i \in A$ 则 $I(j \in A)$ 等于 1，否则它等于 0. 因此，对于 $j\ge 0$ 有
$$
\lambda g(j+1) - jg(j) = I(j \in A) - \sum_{i \in A} e^{-\lambda} \lambda^{i} /i! 
$$
故而
$$
\lambda g(W+1) - Wg(W) = I(W \in A) - \sum_{i \in A} e^{-\lambda} \lambda^{i} /i!
$$
取期望给出
$$
E[\lambda g(W+1) - Wg(W)] = P(W \in A) - \sum_{i \in A} e^{-\lambda} \lambda^{i} /{i!}
$$

我们需要 $g$ 的下述性质，这里略去其证明。
引理 10.2.1 ： 对任意 $\lambda$ 和 $A$ 有：
$$
|g(j) - g(j-1)| \le \frac{1-e^{-\lambda}}{\lambda} \ge \min(1,1/\lambda)
$$
由于对 $i \le j$ 有：
$$
g(j) - g(i) = g(j) - g(j-1)+g(j+1) -g(j-2) \cdots +g(i+1) - g(i)
$$
我们可以从引理 10.2.1 和三角不等式得到：
$$
|g(j) - g(i)| \le |j-i| \min(1,1/\lambda)
$$
我们需要下述引理来继续我们的分析：
引理 10.2.2：对任意随机变量 $R$ 有：
$$
E[WR] = E\left[\sum_{i=1}^{n} RX_{i}\right]= \sum_{i=1}^{n}E[RX_{i}] = \sum_{i=1}^{n}E[RX_{i}|X_{i}=1] = \sum _{i=1}^{n} \lambda_{i}E[R|X_{i}=1]
$$
若在引理 10.2.2 中令 $R = g(W)$，则我们得到：
$$
E[Wg(W)] = \sum_{i=1}^{n}\lambda_{i}E[g(W)|X_{i}=1] = \sum_{i=1}^{n}\lambda_{i}E[g(V_{i}+1)]
$$
其中 $V_{i}$ 是任意一个随机变量，它的分布和在给定 $X_{i}= 1$ 时 $\sum_{j \not = i}X_{j}$ 的条件分布相同，即 $V_{i}$ 是使得
$$
P(V_{i} = k) = P(\sum_{j \not = i}X_{j}=k|X_{i}=1)
$$
的任意随机变量。
由于 $E[\lambda g (W+1)] = \sum_{i=1}^{n} \lambda_{i} E[g(W+1)]$，我们由方程 （10.2.1）和（10.2.3）得：
$$
|P(W \in A) - \sum_{i \in A}e^{-\lambda}\lambda^{i} \frac{}{i!|}= |\sum_{i=1}^{n} \lambda_{i}(E[g(W+1)]-E[g(V_{i}+1)])| = |\sum_{i=1}^{n} \lambda_{i} E[g(W+1) - g(V_{i}+1)]| \le \sum_{i=1}^{n} \lambda_{i}E[|g(W=1) - g(V_{i}+1)|] \le \sum_{i=1}^{n}\lambda_{i}\min(1,1/\lambda)E[|W-V_{i}|]
$$
其中最后的不等式使用了方程（10.2.2）. 所以，我们就证明了下述定理。
定理 10.2.3：令 $W_{i}(i=1,2,\cdots ,n)$ 是任意随机变量，其分布于在给定 $X_{i}(i=1,2,\cdots ,n)$ 时 $\sum_{j\not=i}X_{j}$ 的条件分布相同。即对一切 $i$，$V_{i}$ 使对一切 $k$ 有
$$
P(V_{i}=k) = P(\sum_{j \not = i}X_{i} = k |X_{i} = 1)
$$
则对非负整数的任意子集 $A$ 有：
$$
|P(W \in A) - \sum_{i \in \frac{A}e^{-\lambda}\lambda^{i}}{i!|}\le \min(1,\frac{1}{\lambda})\sum_{i=1}^{n}\lambda_{i}E[|W-V_{i}|]
$$
倘使 $\lambda_{i}$ 很小而 $X_{i}$ 之间只有弱的相依性，Poisson 逼近将是精确的。

例子 10.2（A）：若 $X_{i}$ 是独立的伯努利随机变量，则我们可令 $V_{i} = \sum_{j \not = i}X_{j}$。所以故而：
$$
E[|W-V_{i}|] = E[X_{i}] = \lambda_{i}
$$
故而
$$
|P(W \in A) - \sum_{i \in A \frac{}e^{-\lambda}\lambda^{i}}{i!|}\le \min(1,\frac{1}{\lambda})\sum_{i=1}^{n}\lambda_{i}^{2}
$$
由于在定理 10.2.3 中 Poisson 逼近的界使用具有指定分布的随机变量 $V_{i}$ 给出的，我们可以尝试将 $V_{i}$ 与 $W$ 耦合以简化 $E[|W-V_{i}|]$ 的计算。例如，在很多情形中，$X_{i}$ 是负相关的，故而 $X_{i}= 1$ 的信息僵尸的其他 $X_{j}$ 等于 1 的可能性减少，存在一个导致 $V_{i}$ 小于或等于 $W$ 的耦合。若 $V_{i}$ 与 $W$ 如此耦合，就推出：
$$
E[|W-V_{i}|]  = E[W-V_{i}] = E[W] - E[V_{i}]
$$

例子 10.2（B）：假设有 $m$ 个球放进 $n$ 个瓮中，每个球独立地以概率 $p_{i}(i=1,2,\cdots ,n)$ 放进瓮 $i$ 中，令 $X_{i}$ 是瓮 $i$ 为空这一事件的示性函数，并以 $W = \sum_{i=1}^{n}X_{i}$ 记空瓮数，若 $m$ 足够大，使得
$$
\lambda_{i} = P(X_{i}=1) = (1-p_{i})^{m}
$$
中的每一个都很小，则我们可以预期 $W$ 应该近似地具有均值为 $\lambda = \sum_{i=1}^{n}\lambda_{i}$ 的 Poisson 分布。
因为 $X_{i}$ 具有负相关，由于瓮 $i$ 是空这一事实使得其他瓮也空的可能性减少，所以我们可以假设能构建一个导致 $W \ge V_{i}$ 的耦合。为证明这确实可能，想象这 $m$ 个球按照指定的概率分配，而以 $W$ 记空瓮数。现在我们把瓮 $i$ 中每个球以概率 $p_{j}/(1-p_{i})$ 重新分配到其他瓮中。若现在我们以 $V_{i}$ 记空瓮 $j$ 的个数，则易见 $V_{i}$ 具有定理 10.2.3 中指定的何时分布。由于 $W \ge V_{i}$，这就推出：
$$
E[|W - V_{i}|] = E[W-V_{i}] = E[W] - E[V_{i}] = \lambda - \sum_{j \not = i} (1-\frac{p_{j}}{1-p_{j}})^{m}
$$
于是对任意集合 $A$ 有：
$$
|P(W \in A ) - \sum_{i \in A }e^{-\lambda} \frac{\lambda^{i}}{i!}| \le \min \left(1, \frac{1}{\lambda}\right)\sum_{i=1}^{n}\lambda_{i}\left[\lambda - \sum_{j \not = i }(1- \frac{p_{j}}{1-p_{j}})^{m}\right]
$$

何时 Poisson 逼近误差较小的进一步简介得自于在每个 $i (i=1,2,\cdots ,n)$ 存在一个 $V_{i}$ 和 $W$ 耦合的方法使得 $W \ge V_{i}$ 的情形。因为在此情形，我们有：
$$
\sum_{i} \lambda_{i}  E[|W-V_{i}] = \sum_{i} \lambda_{i}E[W] - \sum_{i}\lambda_{i}E[V_{i}] = \lambda^{2} - \sum_{i}\lambda_{i} (E[1+V_{i}]-1) = \lambda^{2}+\lambda -\sum_{i} \lambda_{i} E\left[1+ \sum_{j \not = i }X_{j}|X_{i}=1 \right]= \lambda^{2}+\lambda - \sum_{i}\lambda_{i}E[W|X_{i}=1] = \lambda^{2}+\lambda - E[W^{2}] = \lambda - Var(W)
$$
其中倒数第二个等式来自引理 10.2.2 中置 $R=W$。
于是我们证明了下述命题：
命题 10.2.4：若对每个 $i(i=12,\cdots ,n)$ 存在一个 $V_{i}$ 和 $W$ 耦合的方法，使得 $W \ge V_{i}$，则对于任意集合 $A$ 有：
$$
|P(W \in A) - \sum_{i \in A}e^{-\lambda} \frac{\lambda^{i}}{i!}| \le \min(1,\frac{1}{\lambda})[\lambda - Var(W)]
$$
于是，粗略地说，在 $X_{i}$ 中出现一个使得其他 $X_{j}$ 出现的可能减少的情形，倘若 $Var (W) = E(W)$，则 Poisson 逼近将是很精确的。

## 10.3 改善 Poisson 逼近
再次令 $X_{1},\cdots ,X_{n}$ 是伯努利随机变量，具有 $\lambda_{i}= P(X_{i}=1 )$。在本节中我们介绍逼近 $W = \sum_{i=1}^{n}X_{i}$ 的概率函数的另一个方法，它基于下述命题：
命题 10.3.1：令 $V_{i}$ 的分布与在给定 $X_{i}=1$ 时 $\sum_{j \not = i}X_{j}$ 的条件分布相同。
（a）$P (W >0) = \sum_{i=1}^{n}\lambda_{i}E[1/(1+V_{i})]$
（b）$P (W = k) = \frac{1}{k} \sum_{i]1}^{n}\lambda_{i}P(V_{i}= k-1)$
证明：两部分都得自引理 10.2.2. 为证明（a），令：
$$
R = 
\begin{cases}
\frac{1}{W} \quad W = k  \\
0 \quad W = 0
\end{cases}
$$
则由引理 10.2.2 我们得到：
$$
P(W >0) = \sum_{i=1}^{n}\lambda_{i}E\left[\frac{1}{W} |X_{i}=1\right]= \sum_{i=1}^{n} \lambda_{i} E[1/(1+V_{i})]
$$
这证明了（a）。为了证明（b），令：
$$
R = 
\begin{cases}
\frac{1}{k}\quad W=k  \\
0 \quad others
\end{cases}
$$
并利用引理 10.2.2 得：
$$
P(W=k) = \sum_{i=1}^{n}\lambda_{i}\frac{1}{k} P(W=k|X_{i}=1) = \frac{1}{k} \sum_{i=1}^{n}\lambda_{i}P(V_{i}=k-1)
$$
令：
$$
a_{i}= E[V_{i}] = \sum_{j \not = i} E[X_{j}|X_{i}= 1]
$$
现在所有的 $a_{i}$ 都很小。且若在给定 $X_{i}=1$ 时余下的 $X_{j}$ 只是“弱”相依的，则 $V_{i}$ 的条件分布近似地是均值为 $a_{i}$ 的 Poisson 分布。假定是这样，则：
$$
P(V_{i}=k-1) \approx \exp(-a_{i})a_{i}^{k-1} \frac{1}{(k-1)!} , k \ge 1
$$
$$
E[\frac{1}{(1+V_{i})}]\approx  \sum_{j}(1+j)^{-1} \exp(-a_{i}) \frac{a_{i}^{j}}{j!} = \frac{1}{a_{i}} \exp(-a_{i})\sum_{j}  \frac{a_{i}^{j+1}}{(j+1)!}  = \exp(-a_{i}) \frac{\exp(a_{i})-1}{a_{i}}= (1-\exp(-a_{i}))/a_{i}
$$
利用上式并结合命题 10.3.1，就得到下面的逼近：
$$
P(W>0)\approx \sum_{i=1}^{n}\lambda_{i} (1-\exp(-a_{i})) \frac{1}{ a_{i}}
$$
$$
P(W=k)\approx \frac{1}{k} \sum_{i=1}^{n} \lambda_{i}\exp(-a_{i}) a_{i}^{k-1} \frac{1}{(k-1)!}, k \ge 1
$$
若 $X_{i}$ 都是“负”相依的，则在给定 $X_{i}=1$ 时，其他 $X_{j}$ 等于 1 的可能性变小。因此，$V_i$ 是伯努利随机变量的和，和的每项均值比 $W$ 作为和的每项均值小，故而我们可以预期它的分布比 $W$ 的分布离 Poisson 分布更近。事实上，在参考文献中已经证明了，当 $X_{i}$ 都是“负”相依时，即使 $\lambda <1$，上述逼近也比通常的 Poisson 逼近更精确。下面的例子对这个命题提供了一些数值上的证据。

例子 10.3（A）：伯努利卷积
假设 $X_{i}(i= 1,2,\cdots ,10)$ 是具有 $E[X_{i}] = i /1000$ 的独立的伯努利随机变量。下面的表给出了在本节中新的逼近与通常的 Poisson 逼近的比较：

| $k$ | $P(W=k)$ | 新的逼近 | 通常的逼近 |
| --- | -------- | -------- | ---------- |
| 0   | 0.946302 | 0.946299 | 0.946485   |
| 1   | 0.052413 | 0.052442 | 0.052056   |
| 2   | 0.001266 | 0.001257 | 0.001431   |
| 3   | 0.000018 | 0.000020 | 0.000026   |


例子 10.3（B）：例子 10.2（B）涉及 $m$ 次独立的多项试验中不出现的结果数，其中每次试验分别以概率 $p_{1},\cdots ,p_{n}$ 出现 $n$ 个可能结果之一。当试验结果 $i(i=1,2,\cdots ,n)$ 不出现时令 $X_{i}= 1$，否则令它为 0. 由于结果 $i$ 不出现使得其他结果不出现的可能性更小，在 $X_{i}$ 之间存在一种负相依性，于是我们可预期由方程（10.3.1）给出的逼近在 $\lambda<1$ 时比直接的 Poisson 逼近更精确，其中
$$
a_{i}= \sum_{j \not = i }E[X_{j}|X_{i}=1] = \sum_{j \not = i} (1- \frac{p_{j}}{1-p_{i}})^{m}
$$
下面的表在 $n=4, m=20$ 和 $p_{i} = i/10$ 时给出了两种逼近的比较。$W$ 是不出现的结果数。

| $k$ | $P(W=k)$ | 新的逼近 | 通常的逼近 |
| --- | -------- | -------- | ---------- |
| 0   | 0.86690 | 0.86689 | 0.87464   |
| 1   | 0.13227 | 0.13230 | 0.11715   |
| 2   | 0.00084 | 0.00080 | 0.00785   |

例子 10.3（C）再次考虑 $m$ 次独立实验，每次试验分别以概率 $p_{1},\cdots ,p_{n}$ 出现 $n$ 个可能的结果之一，但是现在以 $W$ 记至少出现 $r$ 次的结果数。在任意指定的至少出现 $r$ 次的结果是不太可能的情形时，$W$ 粗略地为 Poisson 随机变量。此外，因为 $W$ 的示性随机变量是负相关的（因为结果 $i$ 出现至少 $r$ 次使得其他结果也出现至少 $r$ 次的可能性更小），当 $\lambda <1$ 时新的逼近应该是很精确的。
下面的表在 $n=6,m=10$ 和 $p_{i} = 1/6$ 时给出了两种逼近的比较，$W$ 是至少出现 5 次的结果数。

| $k$ | $P(W=k)$  | 新的逼近  | 通常的逼近 |
| --- | --------- | --------- | ---------- |
| 0   | 0.9072910 | 0.9072911 | 0.91140    |
| 1   | 0.0926468 | 0.0926469 | 0.08455    |
| 2   | 0.0000625 | 0.0000624 | 0.00392    |

命题 10.3.1（a）也可用于得到 $P(W>0)$ 的界。
推论 10.3.2：
$$
P(W>0) \ge \sum_{i=1}^{n} \lambda_{i}/(1+a_{i})
$$
证明：由于 $f (x) = 1/x$ 对 $x\ge 0$ 是凸函数，结论得自命题 10.3.1（a）并利用好 Jensen 不等式。
在推论 10.3.2 中给出的界可能十分精确。例如，在 10.3（A）中它给出了上界 $P (W=0) \le 0.947751$，而准确概率为 0.946302，在例 10.3（B）和例 10.3（C）中它给出了上界 $P (W=0) \le 0.86767$ 和 $P (W=0) \le 0.90735$，两者都小于直接的 Poisson 估计。

