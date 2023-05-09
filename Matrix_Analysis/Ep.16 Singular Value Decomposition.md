#MA 

## 矩阵分析的集大成之作——SVD
引入问题：矩阵的等价定义为：
$$
AP=QB
$$
也就是讨论线性变换 $A$ 在入口基 $P$，出口基 $Q$ 下面的表示为 $B$ 。我们不妨讨论一个特殊的问题：如果 $P$ 和 $Q$ 都是标准正交基，我们能得到什么？
对于 $A \in \mathbb{C}^{m\times n}$，我们希望找到幺正矩阵 $V \in \mathbb{C}^{n\times n}$，$U\in \mathbb{C}^{m\times m}$，使得 $B$ 尽可能地简单！

##### Theorem 
对于任意矩阵 $A$，总能找到 $V,U$，使得
$$
AV = U \mathrm{diag}(\sigma_{1},\sigma_{2},\cdots,\sigma_{r},0,\cdots ,0 )
$$
其中，$r = \mathrm{rank}(A)$，并且，$\sigma_{i} = \sqrt{\lambda_{i}(A^{H}A)}$ ，这些 $\sigma_{i}$ 称为 $A$ 的 $r$ 个奇异值（Singular Values）

##### Proof 
首先，取 $H=A^{H}A$，显然有 $H^{H}=H$，且 $H$ 非负定，且 $\mathrm{rank}(H) = \mathrm{rank}(A)$，那么，显然有
$$
V^{H}HV = \mathrm{diag}(\lambda_{1},\lambda_{2},\cdots ,\lambda_{r},0,\cdots ,0)
$$
其中，$\lambda_{i}$ 是 $H$ 的特征值, $\lambda_{i} \ge 0$ 
变换上式的写法，那么
$$
\mathrm{LHS} = (AV)^H (AV)
$$
记 $AV=B$ ，将 $B$ 进行分割，使得 $B = [b_{1}, b_{2},\cdots ,b_{r}, b_{r+1},\cdots ,b_{n}] ={B_{1},B_{2}}$ ，$B_1$ 包含 $b_{1}$ 到 $b_{r}$，$B_{2}$ 则包含了剩下的部分。那么
$$
LHS = \begin{bmatrix}B_{1}^{H}B_{1} & B_{1}^{H}B_{2}  \\  B_{2}^{H}B_{1} & B_{2}^{H }B_{2} \end{bmatrix}
$$
显然，左右对比，得到右下角的一块是零块，也就是说，$B_{2}=0$，那么 $B_{1}^{H}B_{2}$ 和 $B_{2}^{H}B_{1}$ 都是零块，那么：
$$
B_{1}^{H}B_{1}  = \mathrm{diag}(\lambda_{1},\cdots ,\lambda_{r} )
$$
因此，$b_{1},\cdots ,b_{r}$ 是 $\mathbb{C}^{m}$ 中的正交向量组（不一定是标准的） ，现在我们将其标准化
$$
\tilde b_{i} = b_{i} \frac{1}{||b_{i}||} = b_{i} \frac{1}{\sqrt{\lambda_{i} }} 
$$
再将 $\tilde b_{i}$ 扩充成 $\mathbb{C}^m$ 的一组标准正交基 $\tilde b_{1} ,\cdots ,\tilde b_{r},\beta_{r+1} ,\cdots ,\beta_{m}$ 将它们作为列向量拼成一个幺正矩阵 $U$ 
考虑到
$$
AV = B = [b_{1},b_{2},\cdots b_{r},0,\cdots ,0]=U \mathrm{diag}(\sqrt \lambda_{1},\cdots \sqrt \lambda_{r},0\cdots 0)
$$
也就是说，我们的入口基是通过将 $A^H A$ 进行特征值分解得到的，就是 $A^{H}A$ 的特征向量拼成的矩阵，出口基是通过对入口基进行标准化和扩充之后得到的。至此，我们证成了 SVD 。

### SVD 的性质
- 注： $A^{H}A$ 和 $AA^{H}$ 的非零特征值是一样的。这是因为 $A = U \Sigma V^H$，$A^{H }= U^{H} \Sigma V$ ，计算 $AA^{H}$ 和 $A^{H}A$ 即可验证。

- 接下来，我们可以考虑控制中 SVD 的应用
在 $\mathbb{C}^{n}$ 中找出一组标准正交基 $V$，使得 $x = V \tilde x$ ，在 $\mathbb{C}^{m}$ 中也找到一组标准正交基 $U$，使得 $y =  U \tilde y$ 那么，我们显然可以得到：
$$
\tilde y = \Sigma \tilde x
$$
这实际上是相当于将一个系统解耦

- 最大奇异值的意义
$$\sigma_{i}=\sqrt{\lambda_{\max}(A^{H}A)} = \sqrt{\max_{x \not = 0}\frac{x^{H}A^{H}Ax}{x^{H}x}} = \max \frac{||Ax||}{||x||}
$$
这就代表着 $A$ 这个矩阵对应的线性变换所造成的“最大长度放大率“，也是矩阵的二范数







内积的故事在这里停止。这是我们在“线性代数”中定义的一种非线性运算。依托于内积，我们定义了长度和夹角，解决了最佳逼近问题，研究了标准正交基，G-S 正交化, QR 分解。我们引入了 Hermite 矩阵，考虑了瑞丽商最大化问题，导出了 SVD 分解。可以说，内积这一部分汇集了矩阵分析中的众多夺目的明珠。接下来，我们将研究向量和矩阵的一种固有属性——范数！

































