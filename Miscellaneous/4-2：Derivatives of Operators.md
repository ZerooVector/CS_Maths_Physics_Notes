#MathematicalPhysics 

在前面，我们讨论的算符都是静态的，然而，物理量往往随着时间变化，因此我们应该允许算符也随着时间变化。考虑映射 $H: \mathbb{R} \rightarrow  \text{End}(\mathcal{V})$，一般来说，对于 $t \not = t'$，我们有：$[H (t) , H (t')] \not = 0$。此外，我们还想研究之前提到的 $\exp(H(t))$，其中 $H(t)$ 是一个比 $\exp(H(t))$ 更简单的算符。

既然要研究算符随着时间的变化，我们先来定义算符的导数：对于映射 $H: \mathbb{R} \rightarrow \text{End}(\mathcal{V})$，我们定义它的导数是：
$$
\dfrac{\mathrm{d}H}{\mathrm{d}t} = \lim_{\Delta t \rightarrow 0} \dfrac{ H(t + \Delta t ) - H(t)}{\Delta t }
$$
这个导数也在 $\text{End}(\mathcal{V})$ 中。除了对算符的顺序有要求之外，一般的微分规则也适用于对算符的微分，例如：
$$
\dfrac{\mathrm{d}}{\mathrm{d}t}(UT) = \dfrac{\mathrm{d}U}{\mathrm{d}t}T + U \dfrac{\mathrm{d}T}{\mathrm{d}t}
$$

>[!example]
>计算 $\exp(tH)$ 的导数。

直接计算：
$$
\exp[(t + \Delta t )H] - \exp(tH)  \approx \exp(tH)(1 + H \Delta t) - \exp(t H)  = \exp(t H) H \Delta t
$$
利用 $H$ 和 $\exp(tH)$ 是对易的这一事实，我们立刻得到：
$$
\dfrac{\mathrm{d}}{\mathrm{d}t} \exp(tH) = H \exp(tH)
$$
在推导过程中，我们使用了关系 $\exp (tH) \exp (\Delta tH) = \exp[(t + \Delta t ) H]$，但是一般情况下 $\exp (S+T) \not = \exp (S) \exp(T)$。

如果我们来考虑更加一般的情况：$\exp(H(t))$ 的导数。自然地想到我们需要：
$$
H(t + \Delta t) = H(t) + \Delta t  \dfrac{\mathrm{d}H}{\mathrm{d}t}
$$
之后我们有：
$$
\exp(H(t + \Delta t)) = \exp\left(H(t) + \Delta t  \dfrac{\mathrm{d}H}{\mathrm{d}t}\right)
$$
我们可能想着将其展开，但是其实在一般情况下展开这个是不可能的。

>[!example] 薛定谔方程
>考虑将薛定谔方程 $i \dfrac{\partial }{\partial t} | \psi (t) \rangle = H | \psi(t) \rangle$，我们可以将其转化为一个关于算符的微分方程。

定义传播子 $| \psi (t) \rangle = U (t) | \psi(0) \rangle$，代入原方程后得到：
$$
\dfrac{\mathrm{d}U}{\mathrm{d}t}  = - i H U(t)
$$
我们可以为其找一个级数解，反复对上式求导可以得到 $\dfrac{\mathrm{d}^{n}U}{\mathrm{d}t^{n}} = (-iH)^{n} U(t)$，从而：
$$
U(t) = \left(\sum_{n} \dfrac{(-itH)^{n}}{n!}\right) U(0) = \exp(- i t H) U(0)
$$
由于 $U(0)=1$，那么我们立刻得到 $U (t) = \exp(- i t H)$，很容易注意到 $U (t) U (t)^{\dagger} = 1$，因此传播子是一个幺正算符。

我们现在研究什么时候有 $\exp (S+T) = \exp (S) \exp(T)$。为了简化，我们仅在：
$$
[T,[S,T]] = [S,[S,T]] = 0
$$
的条件下考虑算符：
$$
U(t) = \exp(tS) \exp(tT) \exp[-t(S+T)]
$$
我们可以证明我们给出的简化条件保证了 $[\exp (tT), S] = - t [S, T] \exp(tT)$，从而如果我们计算 $\dfrac{\mathrm{d}U}{\mathrm{d}t}$，可以得到一个简单的微分方程：
$$
\dfrac{\mathrm{d}U(t)}{\mathrm{d}t} = t [S,T] U(t) \Rightarrow  U(t) = \exp\left(\dfrac{t^{2}}{2} [S,T] \right)
$$
从而我们有以下结论：
>[!note]
>在我们给出的简化条件 $[T,[S, T]] = [S,[S, T]] = 0$ 下，有：$\exp (tS)\exp (tT)\exp[t (S+T)] = \exp\left(\dfrac{t^{2}}{2} [S,T]\right)$，这意味着当且仅当 $[S,T]=0$ 时才有 $\exp (tS)\exp (tT) = \exp(t(S+T))$。

现在我们试图研究 $\exp(H(t + \Delta t))$，设 $H(t)$ 和它的导数都与 $[H,\dfrac{\mathrm{d}H}{\mathrm{d}t}]$ 对易， 利用上面的结论立刻得到：
$$
\exp(H(t + \Delta t)) = \exp(H(t)) \exp\left(\Delta t \left(\dfrac{\mathrm{d}H}{\mathrm{d}}t\right)\right) \exp\left(- \dfrac{1}{2}\left[H(t) , \Delta t  \dfrac{\mathrm{d}H}{\mathrm{d}t}\right]\right)
$$
对于无穷小的时间微元：
$$
\exp(H(t + \Delta t)) = \exp(H(t)) \left(1 + \Delta t  \dfrac{\mathrm{d}H}{\mathrm{d}t} - \dfrac{1}{2} \left[H(t), \dfrac{\mathrm{d}H}{\mathrm{d}t}\right]\right)
$$
于是我们有：
$$
\dfrac{\mathrm{d}}{\mathrm{d}t}\exp(H(t)) = \exp(H) \dfrac{\mathrm{d}H}{\mathrm{d}t} - \dfrac{1}{2} \exp(H) \left[H,\dfrac{\mathrm{d}H}{\mathrm{d}t}\right]
$$
上面的推导中，我们令 $S=H (t), T = \Delta t \dfrac{\mathrm{d}H}{\mathrm{d}t}$，交换 $S,T$ 得到：
$$
\dfrac{\mathrm{d}}{\mathrm{d}t} \exp(H(t)) = \dfrac{1}{2} \left( \dfrac{\mathrm{d}H}{\mathrm{d}t} \exp(H) + \exp(J) \dfrac{\mathrm{d} H}{\mathrm{d}t}\right) = \left\{\dfrac{\mathrm{d}H}{\mathrm{d}t}, \exp(H)\right\}
$$
>[!note]
>令 $H : \mathbb{R} \rightarrow \mathcal{L}(\mathcal{V})$ 且 $H$ 以及 $\dfrac{\mathrm{d}H}{\mathrm{d}t}$ 都与 $[H, \dfrac{\mathrm{d} H}{\mathrm{d}t}]$ 对易，那么：$\dfrac{\mathrm{d}}{\mathrm{d}t}\exp (H (t))   = \dfrac{1}{2} \left \{ \dfrac{\mathrm{d}H}{\mathrm{d}t} ,\exp(H) \right\}$。特别地，在 $H$ 与 $\dfrac{\mathrm{d}H}{\mathrm{d}t}$ 对易时有：
> $\dfrac{\mathrm{d}}{\mathrm{d}t} \exp (H (t)) = \exp (H) \dfrac{\mathrm{d}H}{\mathrm{d}t} = \dfrac{\mathrm{d}H}{\mathrm{d}t} \exp(H)$。

一个特别常用的情形是 $F (t) = \exp (tA ) B \exp(-t A)$，其中 $A,B$ 都与时间无关。那么容易得到：
$$
\dfrac{\mathrm{d}F}{\mathrm{d}t} = [A,F(t)] \quad \dfrac{\mathrm{d}}{\mathrm{d}t} [A,F(t)] = \left[A, \dfrac{\mathrm{d}F}{\mathrm{d}t}\right]
$$
那么我们容易推出：
$$
\dfrac{\mathrm{d}^{n}F}{\mathrm{d}t^{n}} = A^{n}  F(t) \quad  A^{n}F(t) = [A,A^{n-1}F(t)]
$$
那么，将 $F(t)$ 在 $t=0$ 处展开：
$$
F(t)  = \sum_{n=0}^{\infty} \dfrac{t^{n}}{n!} \dfrac{\mathrm{d}^{n} F}{\mathrm{d} t^{n} }|_{t=0} = \sum_{n=0}^{\infty}  \dfrac{t^{n}}{n!} A^{n} F(0) = \sum_{n=0}^{\infty}  \dfrac{t^{n}}{n!}A^{n}B
$$
因此我们得到了关系：
$$
\exp(tA) B \exp(- tA) = \left(\sum_{n=0}^{\infty} \dfrac{t^{n}}{n!} A^{n}\right)  B = \exp(tA)B
$$
