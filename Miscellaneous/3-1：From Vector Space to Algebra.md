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
Ab = \left\{x \in A | x = \sum_{k} a_{k}b_{k} ,a_{k} \in A , b_{k} \in B\right\}
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



