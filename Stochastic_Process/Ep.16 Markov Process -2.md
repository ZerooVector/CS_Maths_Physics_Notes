#StochasticProcess 

我们现在会对马尔可夫过程的稳态进行研究。我们希望直接找到一个稳态分布：$\pi_{j}$，它代表着一个状态出现的次数与转移次数之比。我们首先引入一系列概念。

**可达**：从 $i$ 可达 $j$，是说 $\exists n,P_{ij}(n)>0$。直观上，这意味着在有向图上能找到从状态 $i$ 到状态 $j$ 的一条路径。显然，如果 $i$ 可达 $j$，$j$ 可达 $k$，那么一定推出 $i$ 可达 $k$。
**相通**：$i, j$ 是相通的，那么它们互相可达。显然，$i$ 和 $i$ 相通；$i$ 和 $j$ 相通，那么 $j$ 和 $i$ 相通；$i$ 和 $k$ 相通，$k$ 和 $j$ 相通，那么 $i$ 和 $j$ 也相通。显然，相通这个关系有自反性、对称性、传递性，这是一个等价关系。
**闭集**：假定状态空间是 $S$，那么 $S$ 的子集 $C$ 是闭集，是指 $\forall i \in  c  ,j \not \in c$，$i$ 必然不可达 $j$。因此，一个闭集是“进得去，出不来”的。在研究的过程中，一个闭集可以被“约化”成一个状态。
**不可约**：我们称一个马氏链是不可约的，就是说它没有闭真子集。
我们现在要证明一个结论：不可约等价于所有的状态都是相通的。
任取状态 $i$，定义集合 $A_{i} = \{j|i \rightarrow j\}$，我们现在说明 $A_{i}$ 是闭的，结论自然得证。（因为根据不可约的条件，$A_{i}$ 必定是全集。根据 $i$ 的任意性，任取一个状态可达全部状态，因此全部状态相通。）现在，我们需要使用反证法。我们任取 $j\in A_{i}, k \not \in A_{i}$，假如 $j \rightarrow k$，则 $i \rightarrow k$，则 $k \in A_{i}$，我们证明完成。


我们从转移概率矩阵的角度再来认识一下这个问题。我们首先考虑一步转移概率矩阵 $P$，它显然有性质：
- $P_{ij}\ge 0$
- $\sum_{j} P_{ij} =1$
现在我们考虑一个简单性质：如果在马氏链中存在闭集，这个矩阵经过适当的行列变换，可以转换成下面的形状：
![[Pasted image 20240224103338.png]]
显然，有些状态是无法向外转的。注意：闭集里面还可以有闭集，因此这种形状的矩阵可以不断嵌套。因此，最终这个矩阵会变成阶梯型。
![[Pasted image 20240224103652.png]]

我们继续考察一个新的性质：**常返**（Recurrent）。我们现在给出常返的一种定义。首先，我们定义**首达概率**，也就是从 $i$ 出发，首次到达 $j$ 的概率：
$$
f_{ij}(n) = P(X_{n}=j,X_{k} \not = j|X_{0}=i)
$$
它显然有性质：
$$
\sum_{n=1}^{\infty } f_{ij}(n) \le 1 
$$
这是很直观的。这个求和显然最多等于 $1$。（但是证明有点麻烦）接下来，我们可以定义常返：如果 $i$ 是常返态，那么从 $i$ 自身出发，必然会在足够长的时间内返回 $i$：
$$
\sum_{n=1}^{\infty} f_{ii}(n) = 1
$$
这个定义不容易检查，我们需要有更好的判据帮助我们判断常返性，这个判据最好是关于转移概率。我们现在希望将首达概率和转移概率牵线搭桥。一个显然的直观是：
$$
P_{ij}(n) = \sum_{k=1}^{n}f_{ij}(k)P_{jj}(n-k)
$$
这个与 C-K 方程类似，也是对整个过程进行了分解。只不过，这里的分解是从时间上分解（被求和的 $k$ 出现在括号内，找了一个中间时刻，将过程历经的时间分成了两段，再求和）；而 CK 方程是从空间上分解（被求和的 $k$ 出现在下标上，找了一个中间状态，将过程历经的状态分成了两段，再求和），我们同样将对这个方程式给出证明。
我们定义与时间有关的随机变量 $T$，代表着首次到达状态 $j$ 的时间，从而：
$$
\begin{align*}
P_{ij}(n) &= P(X_{n} = j|X_{0}=i)\\
&= \sum_{k=1}^{n}P(X_{n}=j,T_{j}=k|X_{0}=i)\\
&= \sum_{k}P(X_{n}=j,X_{k}=j,X_{k-1}\not =j,\cdots,X_{1}\not=j|X_{0}=i)\\
&= \sum_{k}P(X_{n}=j|X_{k}=j,X_{k-1}\not =j,\cdots,X_{1}\not=j,X_{0}=i)P(X_{k}=j,X_{k-1}\not =j,\cdots,X_{1}\not=j|X_{0}=i)\\
&= \sum_{k}P(X_{n}=j|X_{k}=j,X_{k-1}\not =j,\cdots,X_{1}\not=j,X_{0}=i) f_{ij}(k)\\
&= P_{jj}(n-k)f_{ij}(k)
\end{align*}
$$
同时，注意到上面的方程也数学形式，它显然是某种卷积。于是我们使用卷积和变换的思想来研究它。首先我们可以注意到 $P_{ij}(0) = \delta_{ij}$，$f_{ii}(0)=0$。我们现在希望进行 $Z$ 变换
$$
\begin{align*}
\sum_{n=0}^{\infty} P_{ij}(n) Z^{n} &= \delta_{ij}+\sum_{n=1}^{\infty}P_{ij}(n) Z^{n}\\
&= \delta_{ij}+\sum_{n=1} \left(\sum_{k=1}^{n}f_{ij}(k) P_{jj}(n-k)\right)Z^{n}\\\\
&= \delta_{ij}+ \sum_{n=1} \sum_{k=1} f_{ij}(k)Z^{k} P_{jj}(n-k) Z^{n-k}\\
&= \delta_{ij}+ \sum_{k=1}^{\infty}\sum_{n=k}^{\infty} f_{ij}(k) Z^{k}P_{jj}(n-k) Z^{n-k}\\
&= \delta_{ij} + \sum_{k=1}^{\infty}  f_{ij}(k)Z^{k}  \sum_{n=0}^{\infty} P_{jj}(n) Z^{n}\\
&= \delta_{ij} +P_{jj}(z) F_{ij}(z)
\end{align*}
$$
我们现在给判据：如果 $i=j$，那么：
$$
P_{ii}(z) = 1+P_{ii}(z)F_{ii}(z) \Rightarrow P_{ii}(z) = \dfrac{1}{1-F_{ii}(z)}
$$
再令 $z \rightarrow 1$，我们得到：
$$
\sum_{n}P_{ii}(n)  = \dfrac{1}{1-\sum_{n} f_{ii}(n)}
$$
因此，如果状态 $i$ 是常返态，$\sum_{n}P_{ii}(n)$ 将发散！

我们继续使用上面 Z 变换给出的结果。现在令 $i \not = j$，我们推出：
$$
P_{ii}(z) = F_{ij}(z) P_{jj}(z)
$$
我们仍然令 $z \rightarrow 1$，得到：
$$
\sum_{n=0}P_{ij}(n) = \sum_{n=1} f_{ij}(n) \sum_{n=0} P_{jj}(n)
$$
如果 $j$ 是非常返的，那么显然我们可以看出 $\sum_{n=0} P_{ij}(n)$ 是收敛的，从而 $P_{ij}(n) \rightarrow 0$。因此，直观上，**对于非常返的态，从其他态向着它转移的概率会渐渐趋于 0.**

我们继续考察两个相通的态。我们一定有 $\exists m, P_{ij}(m) >0;\exists n,P_{ji}(n)>0$。假设 $j$ 是常返态，我们给出：
$$
P_{ii}(m+n+k) \ge P_{ij}(m)P_{jj}(k) P_{ji}(n) 
$$
两侧对 $k$ 求和，我们就可以发现 $i$ 也是一个常返态。因此，**相通的状态有相同的常返性**

此外，我们给出另一个性质：**如果一个马氏链只有有限个状态，则我们必然找到一个常返**。直观上这是正确的，现在我们给出证明，由于转移矩阵的性质：
$$
\sum_{j} P_{ij}(n) = 1 \Rightarrow \lim_{ n \rightarrow \infty } \sum_{j} P_{ij}(n) = 1 \Rightarrow \sum_{j} \lim_{n \rightarrow \infty } P_{ij}(n) = 1  
$$
如果全是非常返态，那么 $P_{ij}(n) \rightarrow 0$，上式不可成立。因此，我们完成了证明。因此，**不可约的有限状态马氏链的每个状态均为常返态。**

现在，我们来考虑常返态被访问的次数。我们令 $N_{i}$ 为状态 $i$ 被访问的次数，那么（这里我们使用了示性变量的技巧）：
$$
\begin{align*}
\mathrm{E}(N_{i}|X_{0}= i)\\
&=  \mathrm{E}(\sum_{k}I(X_{k} =i)|X_{0}=i)\\
&= \sum_{k}\mathrm{E}(I(X_{k}=i)|X_{0}=i)\\
&= \sum_{k}P(X_{k}=i|X_{0}=i)\\
&= \sum_{k}P_{ii}(k)
\end{align*}
$$
因此，**一个常返态在足够长的时间内无限次地被访问**。注意：我们上面的过程是从初态为 $i$ 开始的。如果初态不为 $i$，那么我们只需使得马氏链先转移到 $i$，再继续完成上面的证明即可。上述结论不变。

我们再计算一个类似的东西：$P(N_{i} = \infty |X_{0}= i)$。我们定义一个新变量：$g_{ii} = P(N_{i} \ge m|X_{0}= i)$ ，对它进行递推：
$$
\begin{align*}
g_{ii}(m) &= \sum_{k=1}^{\infty} P(N_{i}\ge m，T_{i}=k|X_{0}=i)\\
&= \sum_{k} P(N_{i}\ge m|T_{i}=k,X_{0}=i) P(T_{i}=k|X_{0}=i)\\
&= \sum_{k}P(N_{i}\ge m-1|X_{0}=i)f_{ii}(k)\\
&= \sum_{k}g_{ii}(m-1)f_{ii}(k)
\end{align*}
$$
因此，$g_{ii}(\cdot)$ 是以 $\sum_{k}f_{ii}(m)$ 为公比的等比数列！考虑到 $g_{ii}(0)=1$，那么**对于常返态，它以 1 的概率无穷次地被访问！而对于非常返态，它则以 0 的概率无穷次地被访问。**

我们再看一个前面结论的加强。如果 $i$ 可达 $j$，$i$ 常返，$j$ 也常返吗？我们的证明思路是利用我们的两个条件推出 $j$ 一定可以回到 $i$。（这是一个判断常返态的定性条件，直观来说，从一个常返态 $i$ 到达任意状态 $j$，我们必须能够从 $j$ 回到 $i$）
考虑：
$$
g_{ij}(m) = P(N_{j}\ge  m |X_{0}=i)
$$
我们已经推出 $g_{ii}(\infty)=1$。这次我们使用空间分解。
$$
\begin{align*}
g_{ii}(\infty) &= \sum_{k}P_{ik}(m) g_{ki}(\infty)
\end{align*}
$$
这里，方程左侧是从 $i$ 出发，无穷次访问 $i$ 的概率，使用全概率公式进行分解，拆分成 $i$ 到达 $k$ 的概率和从 $k$ 出发，无穷次访问 $i$ 的概率（因为总次数是无穷次，所以到底从 $i$ 到 $k$ 的路上又访问了几次 $i$，我们不关心）。因为我们 $\exists m, P_{ij}(m) > 0$，又注意到 $\sum_{k} P_{ik}(m) = 1$，从而变形上式得到：
$$
0= \sum_{k} P_{ik}(m)(1 - g_{ki}(\infty))
$$
由于 $P_{ij}(m)>0$，我们推出：
$$
g_{ji}(\infty) = 1
$$
这说明从 $j$ 出发，我们也以 1 为概率，无穷次访问 $i$。从而我们得到 $j$ 可达 $i$，从而 $j$ 和 $i$ 相通，从而 $j$ 也是常返态。




