#MathematicalPhysics 

一个向量空间的自同态 $D : \mathcal{A} \rightarrow \mathcal{A}$ 被称为代数的导数，如果它有性质：
$$
D(ab) = [D(a)]b + a[D(b)]
$$
容易验证数学分析中的导数符合这个定义。此外，对易括号 $D_{A}(B) = [A,B]$ 其实是一个导数，很容易验证其性质：$D_{A}([B, C]) = [(D_{A}B), C] + [B ,(D_{A})C]$ 。
>[!note]
>显然，要证明 $D$ 是代数的导数，只需验证定义式对所有基 $\{e_{i}\}$ 成立。

如果 $\mathcal{A}$ 有单位元 $1$，那么 $D (1) = 0$。

>[!note]
>导数 $D$ 服从莱布尼兹公式：$D^{n}(ab) = \sum_{0}^{n}\begin{bmatrix}n \\ k\end{bmatrix} D^{k}(a) \cdot D^{n-k}(b)$

我们定义 $\text{End}(\mathcal{A})$ 是 $\mathcal{A}$ 上自同态的集合，那么 $\mathcal{A}$ 上的导数是 $\text{End}(\mathcal{A})$ 的子集。如果 $D_{1},D_{2}$ 都是导数，那么容易验证 $\alpha D_{1} + \beta D_{2}$ 是导数，但是 $D_{1}D_{2}$ 不是导数。但是容易验证，$[D_{1},D_{2}]$ 是一个导数。因此：
>[!note]
> $\mathcal{A}$ 上的导数 $\mathcal{D}(\mathcal{A})$ 形成一个代数，这个代数装备的乘积运算就是 $[D_{1},D_{2}]$

设 $\mathcal{A,B}$ 是代数，$\phi: \mathcal{A} \rightarrow \mathcal{B}$ 是一个同态。那么 $D : \mathcal{A} \rightarrow \mathcal{B}$ 被称为 $\phi$ -导数，如果：
$$
D(a_{1} a_{2}) = D(a_{1}) \phi(a_{2}) + \phi(a_{1})
 D(a_{2})$$
 例如，设 $D_{A}$ 是 $\mathcal{A}$ 上的导数，那么 $D = \phi \circ D_{A}$ 是一个 $\phi$ -导数

设 $\mathcal{A}$ 是带有单位元的代数，$\omega$ 是 $\mathcal{A}$ 上的对合，线性变换 $\Omega \in \mathcal{L}(\mathcal{A})$ 被称为 $\mathcal{A}$ 相对于 $\omega$ 的反导数，如果：
$$
\Omega(a_{1}a_{2}) = \Omega(a_{1})\cdot a_{2} + \omega(a_{1}) \cdot  \Omega(a_{2})
$$
特殊地，导数是对恒等映射的反导数。与导数一样，我们可以知道 $\text{Ker} \Omega$ 是 $\mathcal{A}$ 的子代数，$\Omega(i)=0$，以及 $\Omega$ 的行为是完全由其在 $\mathcal{A}$ 的生成元上的行为决定的。

>[!note]
>设 $\Omega_{1},\Omega_{2}$ 是相对于对合 $\omega_{1},\omega_{2}$ 的反导数，设 $\omega_{1}\circ \omega_{2} = \omega_{2} \circ \omega_{1}$ 。此外，$\omega_{1} \Omega_{2}= \pm \Omega_{2} \omega_{1}, \omega_{2} \Omega_{1} = \pm \Omega_{1} \omega_{2}$，那么 $\Omega_{1} \Omega_{2} \pm \Omega_{2} \Omega_{1}$ 是相对于对合 $\omega_{1} \circ \omega_{2}$ 的反导数。


