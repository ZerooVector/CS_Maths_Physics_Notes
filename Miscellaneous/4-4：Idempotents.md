#MathematicalPhysics 

在本小节中部，我们将再次回到线性空间分解的这件事情上。首先考虑一个简单的例子，我们希望将 $(x,y)$ 平面内的一个点变换到 $x$ 轴上，最简单的变换是投影算子：
$$
P_{x}(x,y) = (x,0)
$$
注意到 $P_{x}$ 地方重要性质：它是幂等的。

假设我们的线性空间 $\mathcal{V}$ 能被直和分解到 $r$ 个子空间：
$$
\mathcal{V} = \bigoplus_{i=1}^{r} \mathcal{U}_{i}
$$
定义 $P_{j}$ 是将 $| v \rangle$ 向着 $\mathcal{U}_{j}$ 投影的线性算符，容易证明：
$$
P_{j}P_{k} = \delta_{jk} P_{j} 
$$
换言之，$P_{j}$ 全是幂等的，并且互相正交。因此我们有：
$$
\mathbf{1} | v \rangle  = | v \rangle = \sum_{j}   P_{j} | v \rangle  \Rightarrow \sum_{j}  P_{j} =1
$$
如果 $T \in  \text{End}(\mathcal{V})$ ，且 $\{P_{i}\}$ 是一组互相正交的、完备的幂等算符，那么我们有：
$$
T = \sum_{i=1}^{r}  P_{i}  T = \sum_{i=1}^{r}  T_{i} 
$$
也就是说 $T$ 能写成一系列限制在子空间上的线性算符之和。

对于内积空间，我们定义：$\text{Endf}(\mathcal{V})$ 中的幂等厄米算符被称为投影算符。接下来我们研究：如果 $P_{1},P_{2}$ 都是投影算符，那么 $P_{1} +P_{2}$ 是投影算符的条件是什么？由于：
$$
(P_{1}+P_{2})^{2} = P_{1} + P_{2} + \{P_{1},P_{2}\} \Rightarrow  \{P_{1},P_{2}\} = 0
$$
将上面得到的条件左右各乘以 $P_{1}$，可以得到两个方程：
$$
P_{1}P_{2} + P_{1}P_{2}P_{1}  = 0   \quad  P_{1}P_{2}P_{1} + P_{2} P_{1} =  0  \Rightarrow  [P_{1},P_{2}] = 0 
$$
结合两个条件，我们有：
>[!note]
>设 $P_{1}, P_{2}\in \mathcal{L}(\mathcal{V})$ 是投影算符，则当且仅当 $P_{1},P_{2}$ 正交，$P_{1},P_{2}$ 才是投影算符。

给定某个单位方向向量 $| e \rangle$，容易验证 $P = | e \rangle \langle e |$ 是一个投影算子，因此，给定任意向量 $y$，容易验证向着 $y$ 方向的投影算子为：
$$
P_{y} = \dfrac{|  y \rangle \langle y |}{\langle  y | y \rangle}
$$
给定向量 $| x \rangle$，$P_{y} | x \rangle$ 是沿着 $y$ 方向的分量，而 $(\mathbf{1} - P_{y}) | x \rangle$ 与 $| y \rangle$ 正交的分量。
![[Pasted image 20240822100707.png|500]]
如图，我们称 $| x \rangle$ 被 $| y \rangle$ 反射后的向量为：
$$
P_{y} | x  \rangle - (1 - P_{y}) | x \rangle   =   2 \dfrac{\langle  y |  x\rangle}{\langle  y | y \rangle} | y \rangle - |  x \rangle
$$
为了将这个概念一般化，我们定义投影算符和反射算符：
$$
P_{y} = \dfrac{| y \rangle \langle  y |}{\langle  y| y \rangle} \quad   R_{y} = 1 - 2P_{y}  
$$
$P_{y} | x \rangle$ 给出 $| x \rangle$ 沿着 $| y \rangle$ 的分量，而 $R_{y} | x \rangle$ 给出的是图中相对于垂直于 $| y \rangle$ 的平面的反射。

我们之前已经说过，给定一个向量 $| e \rangle$，我们就能构造投影算符 $| e \rangle  \langle e |$，而当所有的投影算符加起来作用到一个向量上时，这个向量就“复返此身”，那么我们得到了极其重要的：
>[!note] 完备性关系
>设 $B = \{| e_{i} \rangle\}$ 是 $\mathcal{V}_{N}$ 的一组正交基底，那么 $\{P_{i}= | e_{i} \rangle \langle e_{i} |\}$ 是一组互相正交的投影算符，我们有：$\sum_{i=1}^{N} P_{i} = \sum_{i=1}^{N} | e_{i} \rangle \langle e_{i} | = \mathbf{1}$。

如果我们只选取前 $m$ 个向量，那么 $P^{(m)}= \sum_{i=1}^{m} P_{i}$ 将一个向量 $|  x \rangle$ 投影到前 $m$ 个基向量张成的空间中。

我们举一个可以计算的具体例子：
>[! Example]
>计算 $\mathcal{V} = \mathbb{R}^{2}$ 中的投影算符和反射算符。

考虑一个向量 $|  y \rangle = \begin{bmatrix}\eta_{1}   \\  \eta_{2}\end{bmatrix}$，那么向着它投影的算子写成：
$$
P_{y}= \dfrac{ | y \rangle \langle y |}{ \langle  y|y  \rangle} = \dfrac{1}{\eta_{1}^{2}+ \eta_{2}^{2}} \begin{bmatrix}\eta_{1}^{2}  & \eta_{1} \eta_{2}  \\  \eta_{1}\eta_{2} &  \eta_{2}^{2}\end{bmatrix}
$$
如果令：
$$
\dfrac{\eta_{1}^{2}}{\eta_{1}^{2} + \eta_{2}^{2}} = \cos^{2} \alpha \quad  \dfrac{\eta_{2}^{2}}{\eta_{1}^{2} + \eta_{2}^{2}} = \sin^{2} \alpha
$$

那么我们可以将投影算符和反射算符写成：
$$
P_{y}= \begin{bmatrix}\cos^{2} \alpha & \sin \alpha \cos \alpha \\  \sin \alpha \cos \alpha   & \sin ^{2} \alpha\end{bmatrix} \quad  R_{y}= \begin{bmatrix}- \cos 2 \alpha  & - \sin  2  \alpha  \\  - \sin 2 \alpha &  \cos  2 \alpha\end{bmatrix}
$$
注意：这个反射算符就是一个旋转 $-2 \alpha$ 的效果，因此它是一个等距同构。


