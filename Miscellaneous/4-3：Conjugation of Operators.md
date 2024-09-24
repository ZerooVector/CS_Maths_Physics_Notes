#MathematicalPhysics 

我们设 $| b \rangle , | c \rangle \in \mathcal{V}$，并且有 $| c \rangle =  T | b \rangle$。我们知道在对偶空间 $\mathcal{V}^{\star}$ 中有线性泛函 $(| b \rangle)^{\dagger}  = \langle c |$。我们想问，有没有一个与 $T$ 对应的线性算子，它属于 $\mathcal{ L}(\mathcal{V}^{\star})$？（从这个介绍中，你已经发现了伴随和对偶映射是同构的）

>[!note]
>设 $T \in \mathcal{L}(\mathcal{V})$，$| a \rangle , | b \rangle \in \mathcal{V}$，我们将 $T$ 的伴随或者厄米共轭记为 $T^{\dagger}$，定义为 $\langle  a | T  |b \rangle^{\star} = \langle  b | T^{\dagger}  | a\rangle$。

那么上式的左侧可以写成 $\langle  a | c \rangle^{\star}$ 或者 $\langle  c |a  \rangle$，从而有：
$$
\langle c | = \langle b | T^{\dagger}  \rightarrow  (T | b \rangle)^{\dagger} = \langle b | T^{\dagger}
$$
>[!note] 伴随的性质
> -  $(U+T)^{\dagger}  =  U^{\dagger} + T^\dagger$
> - $(UT)^{\dagger} = T^{\dagger} U^{\dagger}$
> - $(\alpha T)^{\dagger} = \alpha^{\star} T^{\dagger}$
> - $(T^{\dagger})^{\dagger}  =T$（这支队有限维向量空间成立）

根据这些性质，我们会发现算符的伴随和复数的共轭是类似的，那么我们自然要寻找一些类似于实数的算符——厄米算符。如果 $H^{\dagger} = H$，我们称 $H$ 是厄米的；如果 $H^{\dagger}= - H$，我们称 $H$ 是反厄米的。

我们将算符 $T$ 在态 $| a \rangle$ 上的均值定义为 $\langle  T \rangle_{a}  = \langle  a | T  | a\rangle$，由于 $\langle  T \rangle = \langle  a | T^{\star}  | a \rangle$，因此，$T$ 是厄米的，意味着期望 $\langle  T \rangle_{a}$ 是实的。对于任意一个算符：
$$
T = \dfrac{1}{2}(T + T^{\dagger}) + \dfrac{1}{2}(T -T^{\dagger})  = X+A
$$
因此可拆分成一个厄米算符和一个反厄米算符。

>[!note]
>内积空间上的算符 $H$ 是厄米的，当且仅当对于任意 $| a \rangle$，$\langle  a |  H |a \rangle$ 都是实数。

我们只证明反向的部分，如果 $\langle  a | H  |a \rangle = \langle  a | H  | a\rangle^{\star} = \langle  a | H^{\star}  | a\rangle$ ，那么了推出 $\langle  a |H - H^{\dagger}   |a \rangle = 0$，从而有 $H = H^{\dagger}$。

一个算符 $A$ 被称为是正的，如果对于 $| a \rangle \not = 0$ 有 $\langle  a |  A | a\rangle \ge 0$，我们称 $A$ 是严格正的，如果对于 $| a \rangle \not = 0$ 有 $\langle  a | A |a \rangle > 0$。

>[!note]
>一个严格正（正定）的算符 $T$ 是可逆的。


我们已经知道二维和三维的旋转是保范数和向量内积的，那么这一点可以被拓展到复内积空间吗？设 $| a \rangle, | b \rangle \in  \mathcal{V}$，$U$ 是 $\mathcal{V}$ 上保内积的算符，那么我们有：
$$
\langle  a' | b' \rangle =(\langle a | U^{\dagger}) (U | b \rangle) = \langle  a |U^{\dagger}U   |b \rangle = \langle  a | \mathbf{1}  |  b\rangle
$$
因此，我们称算符 $U$ 是幺正的，如果 $U^{\dagger}  = U^{-1}$
