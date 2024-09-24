#MathematicalPhysics 

我们使用 $\mathbb{F},\mathbb{K}$ 来代表 $\mathbb{R}$ 或者 $\mathbb{C}$，且 $\mathbb{F} \subseteq \mathbb{K}$ 。若 $\mathcal{V}$ 是 $\mathbb{K}$ 上的线性空间，那么我们将 $\mathbb{K}$ 上的自同态记为 $\mathcal{L}_\mathbb{K}(\mathcal{V})$ 或者 $\text{End}_\mathbb{K}(\mathcal{V})$。设 $\mathcal{A}$ 是 $\mathbb{F}$ 上的一个交换代数，有单位元 $\mathbf{1}_{A}$，我们称 $\mathcal{A}$ 的 $\mathbb{K}$ 表示是同态 $\rho :\mathcal{A} \rightarrow  \text{End}_\mathbb{K}(\mathcal{V})$，也就是从 $\mathbb{F}$ 上的 $\mathcal{A}$ 到 $\mathbb{K}$ 上的自同态的映射。表示 $\rho$ 如果是单射，那么被称为是忠实的。

>[!note]
>一个简单代数的非平凡表示是忠实的。

>[!example] 四元数的表示
>设 $\mathcal{A} = \mathbb{H}$，其中的元素有如下形式：$q  = q^{i}e_{i} , q^{i}\in \mathbb{R}$，找到它在 $\mathcal{L}(\mathbb{R}^{4})$ 的一个表示。

我们可以找到一个矩阵：
$$
\rho(q) = \begin{bmatrix} q_{0} & - q_{1} & - q_{2} & -q_{3}  \\ q_{1} & q_{0}  & -q_{3}  & q_{2}  \\ q_{2} & q_{3} & q_{0} &  -q_{1}  \\ q_{3} &  -q_{2} & q_{1} & q_{0}\end{bmatrix}
$$
容易验证 $\rho (pq) = \rho (q) \rho(p)$，因此 $\rho$ 的确是 $q$ 的一种表示。

我们称 $\mathcal{V}$ 的子空间 $\mathcal{W}$ 是不变的，如果对于表示 $\rho: \mathcal{A} \rightarrow \text{End}(\mathcal{V})$，如果 $\rho (a) | w \rangle \in \mathcal{W}$ 对于所有的 $a \in \mathcal{A}$ 和 $| w \rangle \in \mathcal{W}$ 都成立。一个表示 $\rho$ 被称为不可约的，如果它的稳定子空间只有 $\mathcal{W} = \mathcal{V}$ 和 $\mathcal{W} = \{|  0 \rangle_{\mathcal{V}}\}$。

>[!note]
>令 $\rho : \mathcal{A} \rightarrow \text{End}(\mathcal{V})$ 是一个表示，$| v \rangle$ 是 $\mathcal{V}$ 中的任意非零向量，那么 $\mathcal{W} = \rho (\mathcal{A})| v \rangle = \{| w \rangle\in \mathcal{V},| w \rangle = \rho(a) | v \rangle \ \text{for some }a \in \mathcal{A}\}$ 是 $\mathcal{V}$ 的稳定子空间。特别地，如果 $\rho$ 不可约，那么 $\rho (\mathcal{A})| v \rangle = \mathcal{V}$。

设 $T$ 是从向量空间 $\mathcal{V}_{1}$ 到 $\mathcal{V}_{2}$ 的一个同构，那么称两个表示 $\rho_{1}: \mathcal{A} \rightarrow \text{End}(\mathcal{V}_{1})$ 和 $\rho_{2} : \mathcal{A} \rightarrow \text{End}(\mathcal{V}_{2})$ 是等价的，如果它们满足 $T \circ \rho_{1}(a) = \rho_{2}(a) \circ T$。

设 $\rho,\eta$ 是 $\mathcal{A}$ 在 $\mathcal{U},\mathcal{V}$ 中的表示，我们定义直和和张量积：
$$
(\rho  \oplus \eta)(a) = \rho(a) \oplus  \eta (a) \quad  (\rho  \otimes  \eta )(a) = \rho(a) \otimes  \eta(a)
$$

自然，我们可以考虑表示 $\rho : \mathcal{A} \rightarrow \text{End}(\mathcal{A})$。我们将 $\mathcal{A}$ 的正规表示定义为 $\rho_{L}: \mathcal{A} \rightarrow \text{End}(\mathcal{A})$：$\rho_{L}(a) b = ab$。也就是说此时的表示 $\rho_{L}(a)$ 就是一个算符，将 $b$ 映射到 $ab$。 如果 $\mathcal{A}$ 含有单位元，那么 $\rho_{L}(a) = \rho_{L}(a')$ 意味着 $\rho_{L}(a) | 1 \rangle = \rho_{L}(a') | 1 \rangle$，从而 $a= a'$，从而 $\rho_{L}$ 是单射，从而 $\rho_{L}$ 是忠实的。

$\rho_{L}$ 是 $\mathcal{A}$ 上的左乘，那么 $\mathcal{A}$ 上的右乘是什么？考虑：
$$
\rho_{R}(ab) | c \rangle = cab   = (ca) b = (\rho_{R}(a) | c \rangle) b = (\rho_{R}(b) \rho_{R}(a)) | c \rangle 
$$
因此 $\rho_{R}$ 也是对 $\mathcal{A}$ 的一个正规表示，而且它有性质 $\rho_{R}(ab) = \rho_{R}(b) \rho_{R}(a)$。可以证明，如果 $\mathcal{A}$ 有单位元，那么 $\rho_{R}(a)$ 也是忠实的。

>[!note]
>设 $\mathcal{L}$ 是 $\mathcal{A}$ 的极小左理想，那么 $\mathcal{A}$ 在 $\mathcal{L}$ 中的正规表示：$\rho^{(\mathcal{L})} : \mathcal{A} \rightarrow \text{End}(\mathcal{L})$，具体来说是 $\rho^{(\mathcal{L})}(a) | x \rangle = ax$ ，是不可约的。

证明：注意到 $\rho^{L}(\mathcal{A})| x \rangle = \mathcal{A}x$。因为 $\mathcal{L}$ 是极小的，那么根据第三章的讨论有 $\mathcal{A}x = \mathcal{L}$，从而 $\rho^{L}(\mathcal{A}) | x \rangle = \mathcal{L}$，根据前面的定理，$\rho^{(\mathcal{L})}$ 是不可约的。

>[!note]
>简单代数 $\mathcal{A}$ 的所有不可约表示都是忠实的，并且与 $\rho^{(\mathcal{L})}$ 等价。

上面我们已经说过，一个简单代数的非平凡表示是忠实的。现在设 $\rho: \mathcal{A} \rightarrow \text{End}(\mathcal{V})$ 是一个不可约表示，对于 $x \in \mathcal{L}$ 和 $| e \rangle \in \mathcal{V}$，记 $\rho (x) | e \rangle = | v \rangle$，那么：
$$
\rho(\mathcal{L}) | e \rangle = \rho(\mathcal{A}x) | e \rangle = \rho(\mathcal{A}) \rho(\mathcal{x}) | e \rangle = \rho(\mathcal{A}) | v \rangle = \mathcal{V}
$$
其中，最后一个等号来自表示 $\rho$ 是忠实的这一事实。现在考虑一个线性映射 $T: \mathcal{L} \rightarrow \mathcal{V}$：$T (y) \rho (y) | e \rangle$，那么 $T (\mathcal{L}) = \rho (\mathcal{L}) | e \rangle = \mathcal{V}$，那么 $T$ 是满射。设 $z$ 是 $\mathcal{L}$ 中的非零元素，如果 $z \in \ker T$ ，那么有 $\mathcal{L} = \mathcal{A}z$，并且：
$$
T(L) = \rho(\mathcal{L}) | e \rangle = \rho(\mathcal{A}) \rho(z) | e \rangle = \rho(\mathcal{A}) T(z) = \{0\}
$$
出现了矛盾。因此只能是 $\ker T = \{0\}$，从而 $T$ 既是满射，又是单射，从而是双射。因此我们可以在 $\mathcal{L}$ 和 $\mathcal{V}$ 之间构建一一对应关系。
为了完成证明，最后我们要得到：
$$
T \circ  \rho^{(\mathcal{L})}(a) = \rho(a) \circ T
$$
验证：取 $y \in \mathcal{L}$，那么右手边得到：
$$
\rho(a) \circ T(y) = \rho(a) \circ  T(y) = \rho(a) \rho(y) | e \rangle = \rho(ay) | e \rangle = T(ay)
$$
而左手边：
$$
(T \circ  \rho^{(\mathcal{L})}(a)) y = T (\rho^{(\mathcal{L})}(a)y) = T(ay) 
$$

这直接给出了一个推论：
>[!note]
>简单代数的所有极小左理想是同构的。

>[!note]
>一个半简单代数的两个不可约的表示是等价的，当且仅当它们有相同的核。

证明：在第三章中，我们说过半简单代数可以做直和分解，且分解的每一部分都是它的一个理想：
$$
\mathcal{A} = \bigoplus_{i=1}^{r} \mathcal{J}_{i}
$$
设 $\rho: \mathcal{A} \rightarrow \text{End}(\mathcal{V})$ 是一个不可约的表示。设对于某些 $p$ 有 $0 \not \in x_{p} \in \mathcal{J}_{p}$ 从而 $|  v \rangle = \rho (x_{p}) | e \rangle  \not = | 0 \rangle$，那么：
$$
\mathcal{V} = \rho(\mathcal{A}) | v \rangle = \rho(\mathcal{A}) \rho(x_{p}) | e \rangle = \rho(A x_{p}) | e \rangle \subseteq \rho(\mathcal{J}_{p}) | e \rangle
$$
因此有 $\mathcal{V} = \rho (\mathcal{J}_{p}) | e \rangle$，也就是说，$\mathcal{V}$ 中的任意元素 $| x \rangle$ 可以被写成 $| x \rangle = \rho (y_{p}) | e \rangle$，由于 $\mathcal{J}_{p},\mathcal{J}_{k}$ 的不交性有：
$$
\rho(z_{k}) | x \rangle = \rho(z_{k} y_{p}) | e \rangle = | 0 \rangle
$$
这意味着 $\rho(z_{k})$ 是一个零算符，换言之：
$$
\bigoplus_{i = 1, i \not= p}^{r}  \mathcal{J}_{i} \subseteq \ker \rho
$$
现在设 $\rho|_{\mathcal{J}_{p}}$ 是将 $\rho$ 在 $\mathcal{J}_{p}$ 上的限制，那么 $T:\mathcal{J}_{p} \rightarrow \mathcal{V}$：$T (z_{p}) = \rho (z_{p}) | e \rangle$ 是一个同构。因此，$\rho (z_{p}) = 0$ 意味着 $z_{p} = 0$，也就是说 $\mathcal{J}_{P} \cap  \ker \rho = \{0\}$，这使得我们进一步加强上式：
$$
\bigoplus_{i = 1, i \not= p}^{r}  \mathcal{J}_{i} = \ker \rho
$$
现在考虑两个表示 $\rho_{1},\rho_{2}$ 有相同的核，也就是说：
$$
\ker \rho_{1} = \ker \rho_{2}=  \bigoplus_{i = 1, i \not= p}^{r}
$$
这意味着我们有同构 $T_{1},T_{2}$：
$$
T_{1}(z_{p })= \rho_{1}(z_{p}) | e_{1} \rangle \quad T_{2}(z_{p })= \rho_{2}(z_{p}) | e_{2} \rangle
$$
并且有：
$$
\rho_{1}(\mathcal{J}_{p}) | e_{1}  \rangle = \mathcal{V}_{1} \quad  \rho_{2}(\mathcal{J}_{p}) | e_{2} \rangle = \mathcal{V}_{2}
$$
那么现在构造一个映射 $S = T_{2} \circ  T_{1}^{-1}$，我们可以验证：
$$
S \circ \rho_{1}(a)  = \rho_{2}(a) \circ S
$$

