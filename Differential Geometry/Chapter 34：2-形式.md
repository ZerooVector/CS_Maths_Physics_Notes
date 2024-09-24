#DifferentialGeometry 

我们现在引入 2-形式。2-形式是一个 $(0,2)$ 阶的反对称张量：
$$
\Psi(v,u) = -\Psi(u,v)
$$
自然地，$p$ 形式是一个 $(0,p)$ 阶的反对称张量，交换任意的两个输入向量的位置都会使得其正负号发生改变。我们的目标是逐渐增加 $p$，使得我们逐渐了解微分形式的本质。幸运的是，在 $p=3$ 时，我们几乎就可以揭示微分形式的全部性质了。

一个典型的例子是面积 2-形式。我们定义 $\mathcal{A}(u,v)$ 是以 $u,v$ 为边的平行四边形的有向面积，很容易证明它是一个张量，几何证明如下图：
![[Pasted image 20240823144349.png|500]]

## 楔积
我们之前说过，任意 $(0,2)$ 阶张量可以分解为一个对称张量和一个反对称张量之和。那么我们有：
$$
\phi \otimes \psi = \dfrac{1}{2}[\phi \otimes \psi + \psi \otimes \phi] + \dfrac{1}{2} [\phi \otimes  \psi - \psi \otimes  \phi]
$$
第二部分这个反对称张量就算通过两个 10 形式产生 2-形式，它被称为楔积：
$$
\phi \wedge \psi  = \phi \otimes \psi - \psi  \otimes \phi
$$
容易注意到楔积本身有反对称性：
$$
\phi \wedge \psi = -(\psi\wedge \phi)
$$
以及服从加法分配律：
$$
\phi \wedge (\psi + \sigma) = \phi \wedge \psi + \phi \wedge \sigma
$$
通过取任意 $u,v$ 进行分量计算， 很容易证明，面积 2-形式是 1-形式笛卡尔基的楔积：
$$
\mathcal{A} = dx \wedge dy
$$
我们接下来说一下楔积的几何意义：
![[Pasted image 20240823145625.png|500]]
之前我们已经提过，1-形式可以被可视化为一个平面族，那么我们现在有两个 1-形式，我们可以构建一个从 $\mathbb{R}^{3}$ 到 $\mathbb{R}^{2}$ 的映射：
$$
v \mapsto  F(v) = \begin{bmatrix}\phi(v)  \\ \psi(v)\end{bmatrix}
$$
将楔积 $\phi \wedge \psi$ 应用于 $\mathbb{R}^{n}$ 内的任意平行四边形时，它输出的实数代表着 $F(v_{1}),F(v_{2})$ 形成的平行四边形的有向面积。证明很简单：
$$
\begin{align*}
(\phi \wedge \psi) &= \phi(v_{1})\psi(v_{2}) - \psi(v_{1}) \phi(v_{2})\\
&= \det  \begin{bmatrix}\phi(v_{1} & \phi(v_{2})\\
\psi(v_{1}) & \psi(v_{2})\end{bmatrix}\\
 &= \mathcal{A}[F(v_{1}),F(v_{2})]
\end{align*}
$$
除了直角坐标之外，我们也可以推导极坐标中的 2-形式。我们可以通过直接的计算来完成这个推导 （这个过程中，需要使用外导数的莱布尼兹法则来一步步展开式子）：
$$
\begin{align*}
\mathbf{d}x \wedge  \mathbf{d}y &=  \mathbf{d}(r \cos  \theta) \wedge  \mathbf{d}(r \sin \theta)\\
&= [(\mathbf{d}r)\cos \theta  -  r \sin \theta \mathbf{d} \theta] \wedge [(\mathbf{d}r)\sin \theta + r \cos \theta \mathbf{ d} \theta]\\
&= \cos^{2} \theta r \mathbf{d}r \wedge \mathbf{d} \theta - \sin ^{2} \theta  r \mathbf{d} \theta\wedge  \mathbf{d}r\\
&= r \mathbf{d}r \wedge  \mathbf{d} \theta
\end{align*}
$$
## 基底 2-形式和投影
与 1-形式一样，所有 2-形式自然构成向量空间，因此我们可以寻找这个向量空间的基底。我们要说明：所有 $\mathbf{d}x^{i}\wedge \mathbf{d}x^{j}$，其中 $i<j$ 的 2-形式集合是所有 2-形式的一个基底。
显然，根据基底的数量我们可以知道：$\mathbb{R}^{n}$ 中所有 2-形式的集合是 $\dfrac{1}{2}n(n-1)$ 维的向量空间。
例如，对于二维空间，如果 $\Psi$ 是一般的二维张量，那么它的展开有四项，但是如果它是一个 2-形式，那么它只有一项：
$$
\Psi = \Psi_{12}(\mathbf{d}x \wedge \mathbf{d}y)  = \Psi_{12} \mathcal{A}
$$
在三维空间中也是类似的。现在我们看一下这些基底的几何意义：设 $P$ 是 $\mathbb{R}^{3}$ 中的平行四边形，$\mathcal{A}_{z}$ 是 $P$ 在 $(x,y)$ 面上的正交投影，则 $\mathbf{d}x \wedge \mathbf{d}y$ 作用于 $P$ 的结果是 $\mathcal{A}_{z}$ 的有向面积。
![[Pasted image 20240823152426.png|400]]

## 2-形式与 $\mathbb{R}^{3}$ 中向量的联系：流量
为什么我们在大一学习数学分析时（或大二学习电动力学时），学到的矢量微积分（场论初步）只能在三维空间中运算？一个观察是：只有在三维空间中，2-形式的分量与向量的数量是相同的！

我们将三维空间中的 2-形式展开：
$$
\Psi = \Psi^{1}(\mathbf{d}x^{2} \wedge \mathbf{d}x^{3}) + \Psi^{2}(\mathbf{d}x^{3} \wedge \mathbf{d}x^{1}) + \Psi^{3}(\mathbf{d}x^{1} \wedge \mathbf{d}x^{2}) 
$$
我们可以将三个分量写在一起：
$$
\underline{\Psi} = \begin{bmatrix}\Psi^{1} \\  \Psi^{2} \\ \Psi^{3}\end{bmatrix}
$$
但是注意，$\underline{\Psi}$ 中只是 2-形式的三个分量，它只是“伪装”成了一个矢量的样子！为了看看为什么三维空间中的 2-形式会与一个矢量关联起来，我们现在引入通量的概念。设有一种流体是以 $\underline{\Psi}$ 的速度流过全空间，而 $v_{1},v_{2}$ 两个矢量生成平行四边形 $P$，通量是单位时间内穿过这个面的流体的体积。容易证明 $\Psi(v_{1},v_{2})$ 正是通过 $P$ 的通量：我们记通过 $P$ 的通量是 $\Phi(v_{1},v_{2})$。如果我们构造沿着 $z$ 轴的流场 $\underline{\Psi} = \Psi^{3} e_{3}$，那么穿过 $\mathcal{A}_{3}$ 的流量显然是 $\Psi^{3}\mathcal{A}_{3}$，同时有相等的流量穿过 $P$。重复以上过程，我们就得到了：
$$
\Phi(v_{1}) = \Psi^{1}\mathcal{A}_{!}+ \Psi ^{2} \mathcal{A}_{2} + \Psi^{3} \mathcal{A_{3}} = \Psi(v_{1},v_{2})
$$
在可视化上，如果我们绘制单位时间内流过 $P$ 的流体，那么会得到一个平行六面体，而通量就是这个六面体的体积。
![[Pasted image 20240823163707.png|350]]

## $\mathbb{R}^{3}$ 中向量积和楔积的关系
我们现在将 1-形式与向量联系起来。对于 1-形式：
$$
\phi = \phi_{1}\mathbf{d} x^{1} + \phi_{2} \mathbf{d}x^{2}+ \phi_{3} \mathbf{d}x^{3}
$$
我们将对应的向量表示为 $\underline{\phi} = \begin{bmatrix}\phi_{1}  \\  \phi_{2}  \\ \phi_{3}\end{bmatrix}$，我们现在要说明向量的叉乘（矢量积）是三维空间特有的：给定 $\underline{\phi}$ 和 $\underline{\theta}$，二者夹角 $\theta$，我们定义 $\underline{\phi}$ 和 $\underline{\theta}$ 的向量积指向垂直于两个因子的方向，并且服从右手定则，长度则是两个因子张成的平行四边形的面积，我们要证明它实际上对应于 1-形式的楔积。
为了说明这一点，我们定义一个 2-形式 $\Psi = \phi \wedge \sigma$，那么我们要证明 $\underline{\Psi} = \underline{\phi} \times \underline{\sigma}$。我们记 $n  = \underline{\phi} \times \underline{\sigma}$，那么计算楔积：
$$
\Psi(n,\cdots) = \phi(n) \sigma(\cdots) - \sigma(n) \phi(\cdots) = 0
$$
因此 $\underline{\Psi}$ 与 $n$ 有相同的方向。考虑下面这个通量 2-形式：
$$
\begin{align*}
\Psi(\underline{\phi}, \underline{\sigma}) &= (\phi \wedge \sigma)(\underline{\phi},\underline{\sigma})\\
&= \phi(\underline{\phi}) \sigma(\underline{\sigma}) - \sigma(\underline{\phi})\phi(\underline{\sigma})\\
&= [\mathcal{A}(\underline{\phi},\underline{\sigma})]^{2}
\end{align*}
$$
因此我们证明了 $\underline{\Phi} = \underline{\phi} \times \underline{\sigma}$，也就把 1-形式的楔积与向量叉积联系在了一起。

这样，我们可以从楔积的基本公式推出向量的叉积表达式：

## 法拉第的电磁 2-形式和麦克斯韦的电磁 2·-形式
在经典电动力学里，我们有两个三维的矢量场 $\underline{E} , \underline{B}$，我们将与之相关的 1-形式记为 $\epsilon, \beta$；与之相关的 2-形式记为 $E,B$。我们可以构造所谓法拉第 2-形式：
$$
F = \epsilon \wedge  dt + B
$$
我们将粒子 4-速度向量记为 $u$，粒子的动量记作 $\pi$，固有时记作 $\tau$，那么作用于粒子上的电磁力：
$$
\dfrac{\mathrm{d}\pi}{\mathrm{d} \tau} = qF(\cdots,u)
$$
这是个 1-形式，代表电磁力沿着输入向量方向的大小。特别地，我们将洛伦兹力写为：
$$
\dfrac{\mathrm{d}p}{\mathrm{d}t} = q(\underline{E} + v \times \underline{B})
$$
我们声称 $\star F$ 是 $F$ 的霍奇对偶（当然，我们没有定义它），我们将其称为麦克斯韦 2-形式，它被写为：
$$
\star F = \beta \wedge dt - E
$$
使用它可以简化麦克斯韦方程组，我们将在后续推导。




