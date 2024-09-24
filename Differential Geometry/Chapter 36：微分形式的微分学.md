#DifferentialGeometry 

## 1-形式的外导数
我们将函数 $f$ 视作 0-形式，当外导数算子 $\mathbf{ d}$ 作用于 $f$ 上时，它就产生了 1-形式 $\mathbf{d}f$，它的意义是 $f$ 在每一个可能的方向上变化得多快：
$$
\mathbf{d}f(u) = \nabla_{u}f
$$
因此，我们必须推广外导数 $\mathbf{d}$ 的定义，使之作用在 $p$ -形式 $\Psi$ 上的时候会得到 $(p+1)$ -形式 $\mathbf{d}\Psi$。并且正如 1-形式给出了 $f$ 在某一个方向（输入向量方向）的变化率一样，$p+1$ 形式要给出 $\Psi$ 在 $p+1$ 个方向上的变化率。
我们从最简单的情形开始：如何将外导数算子作用在 1-形式上？外导数一定是某种变化率，为了使得这种变化率有意义，我们首先需要一个 1-形式场 $\phi$，同时有一个向量场 $(u,v)$。现在，我们想知道 $\phi$ 沿着 $u$ 的变化率，但是我们又不能直接把 $\phi$ 对着 $u$ 求导（我们根本不知道这是个啥东西！）我们只能退而求其次（事实上，这是我们唯一的选择）——考虑 $\phi(v)$ 沿着 $u$ 的变化率 $\nabla_{u} \phi(v)$，这个东西至少接受两个向量输出一个数，但是它不是反对称的。我们会尝试将其变成反对称的：$\nabla_{u}\phi (v) - \nabla_{v} \phi(u)$。但是现在仍然存在一个问题：$\phi(v)$ 的变化不仅取决于 $\phi$ 的变化，还取决于 $v$ 的变化。因此，我们必须搞清楚 $u,v$ 对上面的式子产生了什么影响，并且把这些影响完全消除！
考虑一下：
$$
\begin{align*}
\nabla_{u} \phi(v) - \nabla_{v} \phi(u)  &= \nabla_{u} (\underline{\phi} \cdot v ) - \nabla_{v} (\underline{\phi } \cdot u)\\
&= [v \cdot \nabla_{u}\underline{\phi} - u \cdot \nabla_{v} \underline{\phi}]+ \phi([u,v])
\end{align*}
$$
其中 $[u,v]$ 是之前提到的对易子。在第二项中包含对 $u,v$ 的导数，而第一项中却没有！因此，我们把第二项扔掉，取以下式子来定义外导数作用在 1-形式上的结果：
$$
\mathbf{d} \phi(u,v) = \nabla_{u}\phi(v) - \nabla_{v}\phi(u) - \phi([u,v])
$$
但是这个式子形式复杂、含义模糊。要使得其简洁，我们需要移除其中的向量。我们将在笛卡尔基底下书写上面的公式。此外，我们简单地选择向量场 $(u,v)$ 使得不变的，以使得对易子为 0。

$$
\begin{align*}
\mathbf{d} \phi(u,v) &= \nabla_{u}  \phi(v) - \nabla_{v}\phi(u) \\
&= u^{i}\partial_{i} (v^{j} \phi_{j}) - v^{i} \partial_{i} (u^{j}\phi_{j})\\
&= \partial_{i} \phi_{j} [\mathbf{d}x^{i}(u) \mathbf{d}x^{j}(v) - \mathbf{d}x^{j}(u) \mathbf{d}x^{i}(v)]\\
&= \partial_{i} \phi_{j} (\mathbf{d}x^{i} \wedge  \mathbf{d}x^{j})(u,v)\\
\end{align*}
$$
因此，记 $\phi = \phi_{i} \mathbf{d}x^{i}$，我们有：
$$
\mathbf{d} \phi = \partial_{i} \phi_{j}(\mathbf{d}x^{i} \wedge  \mathbf{d}x^{j})
$$
由于 $\mathbf{d}f = \partial_{i} f \mathbf{d}x_{i}$，我们显然可以得到一个更简洁的形式：
$$
\mathbf{d}(\phi) = \mathbf{d}(\phi_{j} \mathbf{d}x^{i})  = \mathbf{d}\phi_{j} \wedge  \mathbf{d}x^{j}
$$


## $p$ -形式的外导数及其莱布尼兹法则
这个结果很容易被推广到 $p$ 形式的外导数上:
$$
\mathbf{d} \Phi = \mathbf{d}(\Phi_{i_{1},\cdots ,i_{p}}  \mathbf{d}x^{i_{1}} \wedge \cdots \wedge  \mathbf{d}x^{i_{p}}) = \mathbf{d}\Phi_{i_{1},\cdots ,i_{p}} \wedge  \mathbf{d}x^{i_{1}} \wedge \cdots \wedge  \mathbf{d}x^{i_{p}} 
$$

接下来我们看一下外导数运算的莱布尼兹法则。不难验证，假如 $\Psi$ 是一个微分形式，$f$ 是个函数，那么有：
$$
\mathbf{d}(f \Psi) = (\mathbf{d}f )\wedge  \Psi  +f \mathbf{d} \Psi
$$
但是对于 $\Phi$ 是 $\deg \Phi$ 形式的时候，莱布尼兹法则的推广不是那么明显：
$$
\mathbf{d}(\Phi \wedge \Psi ) = (\mathbf{d}\Phi) \wedge \Psi + (-1)^{\deg \Phi} \Phi \wedge  (\mathbf{d} \Psi)
$$
我们证明一个简单的情况，之后将其推广：
$$
\begin{align*}
\mathbf{d} (\phi \wedge  \Psi) &= \mathbf{d}([\phi  \mathbf{d}x^{i}] \wedge  [\Psi_{jk} \mathbf{d}x^{j}\wedge  \mathbf{d}x^{k}])\\
&= (\Psi_{jk}  \mathbf{d } \phi_{i} + \phi_{i}\mathbf{d }\Psi_{jk})
 \wedge \mathbf{d}x^{i}\wedge \mathbf{d}x^{j}\wedge  \mathbf{d}x^{k}\\
&= (\mathbf{d} \phi) \wedge  \Psi + (\phi_{i} \mathbf{d} \Psi_{jk} ) \wedge  \mathbf{d}x^{i} \wedge \mathbf{d}x^{j}\wedge  \mathbf{d}x^{k} \\
&=  (\mathbf{d} \phi) \wedge  \Psi - (\phi_{i}  \wedge  \mathbf{d}x^{i} ) \wedge \mathbf{d} \Psi_{jk}\wedge \mathbf{d}x^{j}\wedge  \mathbf{d}x^{k} \\
&= (\mathbf{d}\phi)\wedge  \Psi - \phi \wedge  (\mathbf{d}\Psi )
\end{align*}
$$
注意这里面 $\mathbf{d}\Psi _{jk}$ 的移动，我们要将其移动到所有与 $\Phi$ 有关的部分之后，这就是那个神秘的指数出现的原因。

## 闭形式和恰当形式
我们现在考虑让 $\mathbf{d}$ 算子两次作用在同一个微分形式上，我们就来算最简单的一个：
$$
\begin{align*}
\mathbf{d}^{2} \phi &= \mathbf{d}[\partial _{i} \phi_{j}(\mathbf{d}x^{i}\wedge  \mathbf{d}x^{j})]\\
&= \mathbf{d}[\partial_{i}\phi_{j}] \wedge \mathbf{d}x^{i} \wedge \mathbf{ d}x^{j} \\
&= [\partial_{k}\partial_{i}\phi_{j}] \mathbf{d}x^{k}\wedge  \mathbf{d}x^{i} \wedge  \mathbf{d}x^{j}\\
&= 0
\end{align*}
$$
在推导过程中，我们默认了交换偏导数的顺序不会影响结果。使用类似的计算，以上结果可以被推广至 $p$ -形式：外导数算子作用两次的结果都为 0：
$$
\mathbf{d}^{2}= 0
$$

如果一个形式的外导数为 0，我们称这个形式是闭的：
$$
\mathbf{d}\Upsilon = 0 
$$
如果某个 $p$ -形式是某个 $p-1$ 形式的外导数，那么我们称这个 $p$ -形式是恰当的：
$$
\exists \Psi , \mathbf{d} \Psi  = \Upsilon
$$
若 $\Upsilon$ 是恰当的，那么我们将 $\Psi$ 称为 $\Upsilon$ 的位势。$\Psi$ 不是唯一的，因为假如我们取任意 $p-2$ 形式 $\Theta$，我们都有：
$$
 \Psi \rightarrow \tilde  \Psi  = \Psi + \mathbf{d} \Theta \quad  \Upsilon = \mathbf{d} \tilde \Psi
$$
显然，恰当的形式都是闭的，那么闭形式是否都是恰当的？这需要庞加莱引理：若在一个单连通区域内有 $d \Upsilon = 0$，则存在 $\Psi$，使得 $\mathbf{d} \Psi = 0$。这里有一些关于某个形式是否是闭的的小结论：
- 若 $\Upsilon$ 和 $\Phi$ 是闭的，那么 $\Upsilon \wedge  \Phi$ 也是闭的
- 如果 $\Upsilon$ 是闭的，那么对任意 $\Phi$，$\Upsilon \wedge  \Phi$ 都是闭的
- 如果 $\deg  \Phi$ 是偶数，那么 $\Phi \wedge \mathbf{d} \Phi$ 是闭的
 

在复分析中，我们说一个函数是解析的，其直观意义是该函数是对复数的一个局部伸缩、扭转。函数 $f (z) = u+iv$ 解析的条件是：
$$
i \partial_{x}  f = \partial_{y}  f
$$
写成分量形式就是所谓柯西-黎曼方程：
$$
\partial_{x}u  =\partial_{y} v \quad  \partial_{x}v = - \partial_{y} u  
$$
我们可以使用形式的语言重写这个方程。考虑如下 1-形式：
$$
\begin{align*}
\mathbf{d}(f \mathbf{d}z) &= \mathbf{d}f  \wedge  \mathbf{d}z\\
&= (\partial_{x} f  \mathbf{d}x + \partial_{y} f \mathbf{ d}y) \wedge  (\mathbf{d}x + i \mathbf{d}y)\\
&= (i \partial_{x} f - \partial_{y}f) \mathcal{A}
\end{align*}
$$
其中 $\mathcal{A} = \mathbf{d}x \wedge  \mathbf{d}y$ 是面积 2-形式。因此，若 $f(z)$ 解析，则 $f \mathbf{d}z$ 是闭的，也就是说 $\mathbf{d}(f \mathbf{d}z ) = 0$。

## 用形式做向量运算
我们现在只考虑 $\mathbb{R}^{3}$ 中的微分形式，因为只有在这里，一个 2-形式才“伪装”成一个向量，两个 1-形式的楔积才“伪装”成两个向量的叉乘。
我们写出上面 1-形式的外导数的分量：
$$
\mathbf{d} \phi = \partial_{i} \phi_{i}(\mathbf{d}x^{i} \wedge  \mathbf{d}x^{j})  \Rightarrow  \begin{bmatrix}\partial_{2} \phi_{3} - \partial_{3} \phi_{2}  \\ \partial_{3} \phi_{1} - \partial_{1} \phi_{3}  \\ \partial_{1} \phi_{2} - \partial_{2} \phi_{1} \end{bmatrix} \Rightarrow \nabla  \times  \underline{\phi}   = \mathrm{curl} \underline{\phi} = \begin{bmatrix}\partial_{1}  \\ \partial_{2}  \\ \partial_{3} \end{bmatrix} \times  \begin{bmatrix} \phi_{1}  \\ \phi_{2}  \\ \phi_{3}\end{bmatrix}
$$
因此，如果 $\mathbf{d} \phi = 0$，或者说 $\phi$ 是闭的，就意味着向量场 $\underline{\phi}$ 旋度为 0. 此时，我们可以将闭形式 $\phi$ 描绘成保守场对应的向量，它的意义就是保守场沿路径做功。

接下来，我们还可以看看 2-形式的外导数：
$$
\mathbf{d}\Psi = (\partial_{1} \Psi ^{1} + \partial_{2}\Psi ^{2} + \partial_{3} \Psi ^{3}) (\mathbf{d}x^{1} \wedge \mathbf{d}x^{2} \wedge \mathbf{d}x^{3}) = \begin{bmatrix}\partial_{1}  \\  \partial_{2}  \\ \partial_{3} \end{bmatrix} \cdot \begin{bmatrix}\Psi^{1}  \\  \Psi ^{2}  \\ \Psi ^{3} \end{bmatrix} \mathcal{V}
$$
那么我们就制造出了散度 （3-形式的分量）：
$$
\mathbf{d}\Psi  = ( \mathrm{div} \underline{\Psi } ) \mathcal{V} = (\nabla \cdot  \underline{\Psi }) \mathcal{V}
$$
从外微分的基本恒等式：
$$
\mathbf{d}^{2} = 0
$$
我们也可以拿到很多有趣的结论：将其作用在 0-形式（函数）$f$ 上，得到：梯度无旋：
$$
\nabla \times \nabla  f = 0
$$
将其作用在某个 10 形式上，得到：旋度无源：
$$
\nabla \cdot  (\nabla \times \underline{\phi} ) = 0
$$
我们还可以使用这套语言推导许多矢量分析中的基本结论。考虑到一个基本的小结论：
$$
\phi \wedge \Psi  = (\underline{\phi} \cdot \underline{\Psi }) \mathcal{V}
$$
我们可以推出：
$$
(\nabla \cdot [f \underline{\Psi }]) \mathcal{V} = \mathbf{d}[f \Psi ] = (\mathbf{d}f) \wedge \Psi + f \mathbf{d }\Psi  = [ (\nabla  f) \cdot  \underline{\Psi } + f \nabla \cdot  \underline{\Psi }] \mathcal{V}
$$
其他恒等式可以使用类似方式推出。

## 高度统一的简洁美：麦克斯韦方程
最后，我们宣称我们要像电动力学中一样，将麦克斯韦方程统一成一个方程。我们先从两个无源方程开始。我们使用如下的外导数记号将时间部分和空间部分分离：
$$
\mathbf{d}f  = \mathbf{d}_{S}f  + \mathbf{d}_{t}f
$$
考虑我们之前构造的法拉第电磁 2-形式 ：
$$
F = \epsilon \wedge \mathbf{d} t  +  B 
$$
我们现在要求出它的外导数。一项一项地求（我们用 $\mathcal{Q}$ 表示通量 2-形式）：
$$
\begin{align*}
\mathbf{d}(\epsilon \wedge  \mathbf{d}t) &= \mathbf{d}_{S} (\epsilon)\wedge \mathbf{d}t \\
&= (\nabla \times  \underline{E}) \mathcal{Q} \wedge  \mathbf{d}t
\end{align*}
$$
$$
\begin{align*}
\mathbf{d}B &= \mathbf{d}_{S}B  + \mathbf{d}_{t}B\\
&=  \mathbf{d}_{S}B +  \mathbf{d} t \wedge[\partial_{t} B_{x}(\mathbf{d}y \wedge \mathbf{d}z)+ \cdots ]\\
&= (\nabla \cdot \underline{B})\mathcal{V} + \mathbf{d}t \wedge \partial_{t}  B 
\end{align*}
$$
因此我们有：
$$
\mathbf{d}F = (\nabla \cdot \underline B) \mathcal{V} + [(\nabla \cdot \underline E + \partial_{t}\underline B) \mathcal{Q}] \wedge \mathbf{d}t = 0
$$
也就是说法拉第 2-形式是闭的。换言之，存在一个 1-形式的位势 $A$ 使得：
$$
F = \mathbf{d}A
$$
在处理另外两个方程之前，我们保修引入一个四维时空中的 1-形式：
$$
J = - \rho  \mathbf{d}t + j
$$
由于我们并没有引入霍奇对偶，因此我们不加证明地给出，对于另外两个方程，我们将得到：
$$
\mathbf{d} \star F = 4 \pi \star  J
$$
因此微分形式可以大大简化麦克斯韦方程组的表达！

