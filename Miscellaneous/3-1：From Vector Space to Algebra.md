#MathematicalPhysics 

我们定义 $\mathbb{R}$ 或 $\mathbb{C}$ 上的代数是一个向量空间 $\mathcal{A}$，某个被称作“乘法”的运算对这个向量空间封闭，也就是说 $\mathcal{A} \times \mathcal{A} \rightarrow A$，这种乘法满足线性性和分配律，也就是说：
$$
a(\beta b  +  \gamma c) = \beta ab  + \gamma ac \quad  (\beta b  + \gamma c) = \beta ba  +  \gamma ca
$$
其中 $a, b, c \in \mathcal{A}, \beta , \gamma \in  \mathbb{R} \ or  \  \mathbb{C}$ 。此外，我们称一个代数满足结合律，则 $a (bc) = (ab)c$，满足交换律如果 $ab = ba$。代数的单位元 $1$ 定义为 $a1 = 1a = a$，$a$ 的左逆和右逆定义为 $ba=1$ 和 $ab = 1$。由此，我们可以推出代数的一些性质：
- 具有零元：在上面的定义中，令 $b = c, \beta = 1 = - \gamma$ 即可立刻得到 $a0=0a=0$
- 具有唯一的单位元：不妨设有两个单位元 $1,e$，则 $1e=1$，因为 $e$ 是单位元；而 $1e=e$，因为 $1$ 是单位元，从而 $e=1$
- 若某个代数有结合律，则左逆和右逆相等：$bac = (ba) c = b(ac)$
因此，我们显然地得到以下定理：
>[!note]
> $\mathcal{A}$ 是带有单位元的、结合律成立的代数，如果 $a \in \mathcal{A}$ 有左逆和右逆，那么它们相等且这个逆唯一。如果 $a,b$ 均可逆，那么 $(ab)^{-1} = b^{-1}a^{-1}$。

一个代数可以有子代数。设 $\mathcal{A}$ 是一个代数，$\mathcal{A}'$ 是 $\mathcal{A}$ 的线性子空间，那么我们称 $\mathcal{A}'$ 是 $\mathcal{A}$ 的子代数。设 $\mathcal{A}$ 是一个满足结合律的代数，$S$ 是 $\mathcal{A}$ 的子集，那么由 $S$ 诱导出的子代数是 $s_{1}s_{2}\cdots s_{k} ,s_{i} \in S$ 的线性组合。如果 $S$ 中只有一个元素 $s$，那么子代数就是 $s$ 的多项式。考虑到子代数必须满足对乘法的封闭性，这是显然的。

代数 $\mathcal{A}$ 的中心是那些与其他所有元素都可交换的元素