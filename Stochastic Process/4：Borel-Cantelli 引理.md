#StochasticProcess 

给定事件序列 $\{A_{n}\}$，我们定义其上极限：
$$
\{A_{n}\ i.o.\} = \lim \sup_{K \rightarrow \infty} A_{n} = \bigcap_{n=1}^{\infty} \bigcup_{k=n }^{\infty} A_{k}
$$
我们希望考察 $\{A_{n}\ i.o.\}$ 是否一定发生，有如下引理：
>[!note] Borel-Cantelli 引理
>如果 $\sum_{n} P (A_{n}) < \infty$，那么 $\mathbb{P}(\{A_{n}\ i.o.\}) = 0$
>如果 $\sum_{n} P (A_{n}) = \infty$，且 $A_{n}$ 互相独立，那么 $\mathbb{P}(\{A_{n}\ i.o.\}) = 1$

证明：对于 a)，直接计算：
$$
\mathbb{P}\left(\bigcap_{n=1}^{\infty} \bigcup_{k=n }^{\infty} A_{k}\right) \le \mathbb{P}\left( \bigcup_{k=n }^{\infty} A_{k}\right) \le \sum_{k=n}^{\infty} \mathbb{P}(A_{k}) 
$$
在 $n \rightarrow  \infty$ 时，最右侧一项趋于 0.
对于 b)，计算：
$$
\mathbb{P}\left(\bigcup_{k=n}^{\infty} A_{k}\right) = 1 - \mathbb{P}\left(\bigcap_{k=n}^{\infty} A_{k}^{c}\right) = 1 - \prod_{k=n}^{\infty} \mathbb{P}(A_{k}^{c}) = 1- \prod_{k=n}^{\infty} (1- \mathbb{P}(A_{k}))
$$
利用 $1-x \le \exp(-x)$ 有：
$$
\mathbb{P}\left(\bigcup_{k=n}^{\infty} A_{k}\right)  \ge 1 - \prod_{k=n}^{\infty} \exp(- \mathbb{P}(A_{k})) = 1
$$

我们可以对这个定理做一些应用。例如我们证明如下引理：
>[!note]
>设 $\{X_{n}\}$ 是一列独立同分布的期望有限的随机变量，那么 $\dfrac{X_{n}}{n}$ 在 $n \rightarrow \infty$ 时几乎处处收敛到 0.

证明：对于任意 $\epsilon > 0$，定义一列事件：$A_{n}^{\epsilon} = \{\omega \in \Omega : |\dfrac{X_{n}(\omega)}{n}| > \epsilon\}$ ，那么计算：
$$
\begin{align*}
\sum_{n=1}^{\infty} \mathbb{P}(A_{n}^{\epsilon)}&= \sum_{n=1}^{\infty} \mathbb{P}(|X_{n}| > n \epsilon)\\
&= \sum_{n=1}^{\infty} \mathbb{P}(|X_{1}| >n\epsilon )\\
&= \sum_{n=1}^{\infty}\sum_{k-n}^{\infty} \mathbb{P}(k\epsilon<|X_{1}|\ge(k+1)\epsilon)\\
&= \sum_{k=1}^{\infty}k \mathbb{P}(k\epsilon<|X_{1}|\le(k+1)\epsilon )\\
&= \sum_{k=1}^{\infty}k \int_{k \epsilon <|X_{1}|\le(k+1)\epsilon } \mathbb{P}(d \omega)\\
&\le \dfrac{1}{\epsilon}\sum_{k=1}^{\infty} \int_{k \epsilon <|X_{1}|\le(k+1)\epsilon }|X_{1}| \mathbb{P}(d \omega)\\\\
&= \dfrac{1}{\epsilon} \int_{\epsilon<|X_{1}|}|X_{1}| \mathbb{P}(d \omega) < \infty 
\end{align*}
$$
现在定义：$B_{\epsilon}= \{\omega \in \Omega: \omega \in A_{n}^{\epsilon} \ i.o.\}$，也就是 $n \rightarrow \infty$ 时仍然不收敛的那些点。根据引理，显然有 $\mathbb{P}(B_{\epsilon})= 0$，再取遍任意 $\epsilon$，记 $B = \cup_{n=1}^{\infty} B_{\frac{1}{n}}$，那么 $\mathbb{P}(B) = 0$，也就是说除了 $B$ 中之外的点，都收敛。得证。

我们还可以补上之前研究各种收敛之间的关系的时候剩下的内容：依概率收敛的随机变量列中可以选出一个几乎处处收敛的子列。不失一般性，我们设 $X=0$ 。我们这样选取子列的下标：
$$
\mathbb{P}\left(|X_{n_{k}}| \ge \dfrac{1}{k}\right) \le  \dfrac{1}{2^{k}}
$$
对于任意 $\epsilon$，都存在一个 $k_{0}$ 使得 $\dfrac{1}{k_{0}} \le \epsilon$，那么我们有：
$$
\begin{align*}
\sum_{k=1}^{\infty} \mathbb{P}(|X_{n_{k}}| \ge \epsilon)  &\le \sum_{k=1}^{k_{0}}\mathbb{P}(|X_{n_{k}}| \ge\epsilon) + \sum_{k=k_{0}+1}^{\infty}\mathbb{P}\left(|X_{n_{k}}\ge \dfrac{1}{k}|\right) <\infty
\end{align*}
$$
因此 $\mathbb{P}(|X_{nk}|\ge \epsilon,\ i.o.) = 0$，从而不收敛的点的测度为 0. 得证。

