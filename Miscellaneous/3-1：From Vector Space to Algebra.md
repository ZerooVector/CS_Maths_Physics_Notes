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

代数 $\mathcal{A}$ 的中心是那些与其他所有元素都可交换的元素，记作 $Z(A)$。如果 $\mathcal{A}$ 是满足结合律的，那么 $Z(A)$ 是 $\mathcal{A}$ 的子代数。一个带有单位元的代数被称为是中心的，如果 $Z (A) = \text{Span}(1)$。

如果 $A,B$ 是 $\mathcal{A}$ 的子集，那么 $AB$ 表示：
$$
AB = \left\{x \in \mathcal{A} | x = \sum_{k} a_{k}b_{k} ,a_{k} \in A , b_{k} \in B\right\}
$$
我们将 $\mathcal{A}^{2}$ 称为 $\mathcal{A}$ 的诱导代数。

如果在代数 $\mathcal{A}$ 中，$a \times b = ab$，我们将 $a \times b = ba$ 的代数称为其反代数 $A^{op}$。

我们举出一些代数的例子：复数乘法、$n \times n$ 矩阵的乘法、线性空间 $V$ 上算子的复合、对易括号、多项式的乘法（这是一个无穷维的代数）、定义在 $C^{r}(a,b)$ 上函数的乘法 $(fg)(t)  = f(t)g(t)$（这也是一个无穷维的代数）

我们接下来定义代数的直和。为了使得代数的直和 $\mathcal{A} \oplus \mathcal{B}$ 也成为一个代数，我们需要在上面定义一个乘法：
$$
(a_{1}  \oplus b_{1})(a_{2} \oplus b_{2}) = (a_{1} a_{2} \oplus b_{1}b_{2})
$$
这意味着 $a_{1},a_{2}$ 与 $b_{1},b_{2}$ 先在原来的代数上做乘积，再直和起来。一个特殊的情形是：$a \in \mathcal{A}$ 可以被表示为 $a \oplus 0$，而 $b \in  \mathcal{B}$ 可以被表示为 $b \oplus 0$，那么此时 $ab = 0$。

如果 $a \oplus b$ 是 $\mathcal{A} \oplus \mathcal{B}$ 的中心，那么我们有：
$$
(a \oplus b) (x \oplus y) = (x \oplus y) (a \oplus b) \quad  \forall x \in \mathcal{A}, y \in \mathcal{B}
$$
或者 $(ax - xa) \oplus (by - yb) = 0 \Rightarrow ax - xa = 0, by -0 yb = 0$。这意味着 $a \in Z (\mathcal{A}), b \in  Z(\mathcal{B})$，从而：$Z (\mathcal{A} \oplus \mathcal{B}) = Z (\mathcal{A}) \oplus Z(\mathcal{B})$

我们接下来定义代数的张量积。同理，如果我们要求代数的张量积也成为一个代数，我们需要定义乘法：
$$
(a_{1} \otimes b_{1}) (a_{2} \otimes b_{2}) = (a_{1}a_{2}) \otimes (b_{1}b_{2})
$$
由于 $\mathcal{A} \otimes \mathcal{B}$ 和 $\mathcal{B} \otimes \mathcal{A}$ 的同构关系，我们要求 $a \otimes b = b  \otimes a,\forall a,b$。

接下来我们定义一个代数的结构常数。设代数 $\mathcal{A}$ 的基底为 $B = \{e_{i}\}$，我们可以写出：
$$
e_{i}e_{j} = \sum_{k=1}^{N}  c_{ij}^{k} e_{k} \quad c_{ij}^{k}\in \mathbb{C}
$$
$c_{ij}^{k}$ 称为代数 $\mathcal{A}$ 的结构常数。如果给我们 $N$ 维向量空间，我们通过选出一组基和 $N^{3}$ 个结构常数就能将其变成一个代数。

如果一个有单位元的代数中所有非零元素都有逆，那么这个代数被称为除法代数。

举一个可能比较常见的例子：如果我们有四个基 $e_{0},e_{1},e_{2},e_{3}$，我们指定结构常数：
$$
e_{0}^{2} = - e_{1}^{2} = - e_{2}^{2} = - e_{3}^{2} = e_{0}\quad  e_{0}e_{i} = e_{i}e_{0} = e_{i} ,i = 1,2,3 \quad  e_{i}e_{j} = \sum_{k=1}^{3} \epsilon_{ijk} e_{k}, i \not  = j 
$$
这样形成的代数称为四元数的代数，我们通常使用 $1$ 代表 $e_{0}$，而使用 $i,j,k$ 代表 $e_{1},e_{2},e_{3}$，并将四元数记作 $q = x + iy + jz + kw$。

利用与研究直和的代数时类似的思想，我们立刻可以得到：
$$
Z(\mathcal{A}\otimes \mathcal{B}) = Z(\mathcal{A}) \otimes Z(\mathcal{B})
$$

若 $\mathcal{A}$ 是可交换的代数，则 $\mathcal{A}$ 的生成元 $S$ 定义为这样的子集：$\mathcal{A}$ 中的全部元素可以由 $S$ 中元素之积的线性组合表出。例如，$(\mathbb{R}^{3} ,\times)$ 的一个生成元是 $\{\hat e_{x} , \hat e_{y}\}$。

类比从一个线性空间到另一个线性空间的线性映射，我们可以定义代数的同态。设 $\mathcal{A}$ 和 $\mathcal{B}$ 是代数，那么线性映射 $\phi:\mathcal{A} \rightarrow \mathcal{B}$ 若满足 $\phi (\mathcal{A}\mathcal{B}) = \phi (\mathcal{A}) \phi(\mathcal{B})$，则被称为是一个同态。一个代数自身到自身的同态称为自同态。
>[!note] 
>如果 $\mathcal{A}$ 和 $\mathcal{B}$ 是代数，设 $\{e_{i}\}$ 是 $\mathcal{A}$ 的一组基，那么 $\phi$ 是同态，当且仅当 $\phi (e_{i}e_{j}) = \phi (e_{i}) \phi(e_{j})$

证明是简单的，设 $a = \sum_{i} \alpha_{i}  e_{i} , b = \sum_{j} \beta_{j} e_{j}$，直接计算即可证明。

若 $\mathcal{A},\mathcal{B}$ 都是有单位元的代数，同态 $\phi:  \mathcal{A} \rightarrow \mathcal{B}$ 有性质 $\phi (1_{A}) = 1_{B}$，那么称 $\phi$ 是单位的。

>[!note] 
>若 $\mathcal{A,B}$ 是有单位元的代数，且同态 $\phi:\mathcal{A} \rightarrow \mathcal{B}$ 是满射，那么 $\phi$ 必然是单位的。

这很好证明。首先，由于 $\phi$ 是满射，所以必然有 $\mathcal{A}$ 中的元素被映射到 $1_{B}$。其次，如果 $1_{A}$ 不被映射到 $1_{B}$，那么下式不成立：
$$
\phi(\alpha) = \phi(1 \alpha) = \phi(1) \phi(\alpha) = 1 \phi(\alpha)
$$

如果一个向量空间 $\mathcal{V}$ 上的自同态 $\omega$ 满足 $\omega^{2} = 1$，我们称 $\omega$ 是一个对合。（involution，内卷），它有性质 $\omega (a) = e$。这是因为，假设 $\omega (e) = a$，那么我们必须有 $\omega (a) = e$，从而：
$$
\omega(ea) = \omega(e) \omega(a) = \omega(e)e = \omega(e)
$$
在两侧再作用一次 $\omega$，我们得到 $ea = e$，从而 $a = e$。

>[!note] 
>设 $\mathcal{U},\mathcal{V}$ 是两个同构的向量空间，则 $\mathcal{L}(\mathcal{U}),\mathcal{L}(\mathcal{V})$ 是同构的代数。

证明：设 $\phi: \mathcal{U}\rightarrow \mathcal{V}$ 是线性空间的同构，容易构造出代数同构映射：
$$
\psi(T) = \phi \circ T \circ  \phi^{-1}
$$






