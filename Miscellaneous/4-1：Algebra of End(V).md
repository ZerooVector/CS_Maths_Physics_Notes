#MathematicalPhysics 

在这一小节中，我们考虑的集合是 $\text{End}(\mathcal{V})$，也就是 $\mathcal{V}$ 上的自同态。这个集合上装备的乘法运算就是代数同态的复合。$\text{End}(V)$ 有一个单位元 $1$，满足 $\mathbf{1} | \alpha \rangle = | \alpha \rangle$。因此，$\text{End}(\mathcal{V})$ 上的代数是一个带有单位元的代数。另外，一般来说只有双射才能找到逆映射，因此往往只有向量空间的自同态才有逆，一个自同态 $T$ 的逆 $T^{-1}$ 满足 $T \circ T^{-1} = \mathbf{1}$。利用第三章中得到的结论，我们有：

>[!note]
>一个线性算子的逆是唯一的。如果 $T$ 和 $S$ 是 $\mathcal{V}$ 上方的两个可逆线性算子，那么 $TS$ 是可逆的，并且 $(TS)^{-1} = S^{-1} T^{-1}$。

>[!note]
> $T \in \text{End}(\mathcal{V})$ 是可逆的，当且仅当它将 $\mathcal{V}$ 的一个基底映射到另一个基底。

设 $\mathcal{V}_{1},\mathcal{V}_{2}$ 是向量空间，$\mathcal{L}(\mathcal{V}_{1}),\mathcal{L}(\mathcal{V}_{2})$ 是 $\mathcal{V}_{1},\mathcal{V}_{2}$ 上的自同态，那么 $\mathcal{L}(\mathcal{V}_{1} \otimes \mathcal{V}_{2})$ 上的自同态定义为：
$$
\mathcal{L}(\mathcal{V}_{1} \otimes  \mathcal{V}_{2}) = (\mathcal{L}_{1} \otimes  \mathcal{L}_{2})(\mathcal{V}_{1} \otimes  \mathcal{V}_{2}) = \mathcal{L}_{1}(\mathcal{V}_{1} ) \otimes  \mathcal{L}_{2}(\mathcal{V}_{2})
$$
例如：$\mathcal{V}_{1} = \mathbb{C},\mathcal{V}_{2} = \mathcal{V}$ ，那么：
$$
\mathcal{L}(C \otimes \mathcal{V}) = \mathcal{L}(\mathcal{V}^{\mathbb{C}})
$$
这里 $\mathcal{V}^\mathbb{C}$ 是 $\mathcal{V}$ 的复化。

现在我们考虑算子的多项式。对于 $T \in \text{End}(\mathcal{V})$，我们可以构建这样的多项式：
$$
p(T) = \alpha_{0} \mathbf{1}  + \alpha_{1}  T   + \alpha_{2} T^{2} + \cdots  + \alpha_{n} T^{n} 
$$
例如，以下 $T$ 使得二维平面上的向量旋转 $\theta$ ：$T_{\theta}(x, y) = (x \cos  \theta  - y \sin \theta, x \sin  \theta + y \cos  \theta)$，那么 $T_{n \theta}$ 就是使得向量旋转 $n \theta$ 度：$T_{n \theta} = (x \cos n \theta - y \sin  n \theta  ,  x \sin  n \theta + y \cos  n  \theta)$。利用这些多项式，我们可以构造算子的函数：
$$
f(T) = \sum_{k=0}^{\infty}  \dfrac{\mathrm{d}^{k} f}{\mathrm{d}  x^{k}}|_{x = x_{0}} \dfrac{(T - x_{0}\mathbf{1})^{k}}{k!}
$$
最常用的情况可能是指数函数：
$$
\exp(T) = \sum_{k=0}^{\infty} \dfrac{T^{k}}{k!}
$$
我们举一个小例子：
>[!example]
>考虑算子 $T : \mathbb{R}^{2}  \rightarrow  \mathbb{R}^{2}$，$T (x, y) = (-y,x)$，计算 $\exp(\alpha  T)$。

首先注意到：$^{2n} = (-1)^{n} \mathbf{1} ,T^{2n+1} = (-1)^{n} T$ ，从而我们可以将 $\exp(\alpha T)$ 拆分成奇数项和偶数项计算：
$$
\begin{align*}
\exp(\alpha T) &=  \sum_{k=0}^{\infty} \dfrac{\alpha^{2k+1}  T^{2k+1}}{(2k+1)!} + \sum_{k=0}^{\infty} \dfrac{\alpha^{2k} T^{2k}}{(2k)!}\\
&= \sum_{k=0}^{\infty}\dfrac{(-1)^{k}\alpha^{2k+1}}{(2k+1)!}T + \sum_{k=0} ^{\infty} \dfrac{(-1)^{k} \alpha^{2k}}{(2k)!} \mathbf{1}\\
&= T \sin \alpha  + \mathbf{1} \cos  \alpha
\end{align*}
$$
因此最后得到：
$$
\exp(\alpha T)(x,y) = (x \cos  \alpha - y \sin \alpha , x \sin \alpha   + y  \cos  \alpha )
$$
竟然代表二维空间中的旋转！这里的 $T$ 称为旋转的生成元。

我们知道，两个算子相乘的结果一般与顺序有关，但是，如果对于 $T, U \in \mathcal{L}(\mathcal{V})$，有 $UT = TU$，我们就称 $U,T$ 是对易的。对易子 $[U, T] = UT - TU$ 具有以下性质：
![[Pasted image 20240818161322.png]]
一个推论是 $[A, A^{m}] = 0$，其中 $m = \cdots,-2,-1,0,1,2,\cdots$。



