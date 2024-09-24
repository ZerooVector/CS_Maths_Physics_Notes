#DifferentialGeometry 

## 1-形式的线积分
流体沿着定向曲线 $K$ 的环流量，或者粒子沿着曲线 $K$ 运动时，外力场所做的功为：
$$
C_{k} (\underline\phi) = \int_{K} \underline\phi \cdot  dr 
$$
我们显然可以使用形式的语言来重写这个式子，令 $\phi$ 是与力场相关的 1-形式，我们有：
$$
\phi(dr) = \underline \phi \cdot dr = \phi_{K} ds
$$
注意：这里的 $dr,ds$ 只是一般的向量微元和长度微元，而不是 1-形式。这样，我们可以给出 1-形式的线积分的定义：
$$
\int_{K} \phi = \int_{K} \phi(dr) = \int_{K} \phi_{K}  ds
$$
![[Pasted image 20240824165853.png]]
此外，假设积分与路径无关，显然我们有：
$$
\int_{L} \phi = \int_{K_{1} - K_{2}} \phi = \int_{K_{1}} \phi - \int_{K_{2}} \phi  = 0
$$
反过来也是一样的。因此路径的无关性与环路上的积分为 0 可以互相推出。特别地，如果 $\phi$ 是恰当的，也就是说存在 $f$ 使得 $\phi = \mathbf{d}f$，那么：
$$
\phi(\delta r) = \mathbf{d}f(\delta r) = \delta f  
$$
因此：
$$
\int_{K} \phi = \int_{K} \mathbf{d}f = f(b) - f(a)
$$
我们有 $\underline\phi = \nabla  f$，这里的 $\underline\phi$ 是力场，而 $f$ 就是势能。

## 外导数是一个积分
在一般的微积分中，显然导数和积分互为逆运算。不过我们马上就会看到：外微分是在闭环曲线或者封闭曲面上的积分，而不是积分的逆。
我们先考虑 1-形式的外导数：设 $\Pi(\epsilon u ,\epsilon v)$ 为一个平行四边形的有向边界，我们考虑一个 1-形式 $\phi$ 环绕 $\Pi$ 的积分：
$$
\Omega(\epsilon u , \epsilon v) = \oint_\Pi\phi
$$
接下来我们要证明这个东西是 $\phi$ 的外导数：
$$
\Omega(\epsilon u ,\epsilon v) = \mathbf{d} \phi(\epsilon u,\epsilon v)
$$
因此，我们只要将 1-形式沿着任意的平行四边形积分一圈，就得到了它的外导数！显然，我们希望使用不变的向量场 $u,v$，这样平行四边形自然是封闭的，$u,v$ 之间的对易子也是 0。但是注意：在计算这个积分的时候，我们不能从每个边上随意取一个点，然后使用黎曼和来计算这个结果——因为本来我们期望得到的结果就是 $\epsilon^{2}$ 量级的，我们这样随意取点又会引入 $\epsilon^{2}$ 量级的误差。因此，我们选择每条边的中点来完成这个黎曼和的计算。我们设 $a,b,c,d$ 分别为四条边的终点，那么我们有：
$$
\begin{align*}
\Omega(\epsilon u, \epsilon v) &= \phi_{a}(\epsilon u) + \phi_{b}(\epsilon v) + \phi_{c}(- \epsilon u) +\phi_{d} (- \epsilon v)\\
&= [\phi_{b}(\epsilon v) - \phi _{d}(\epsilon  v)] - [\phi_{c}(\epsilon v) - \phi_{a}  (\epsilon v)]\\
&= \nabla_{\epsilon u} \phi(\epsilon v) - \nabla_{\epsilon v} \phi(\epsilon u)\\
&= \mathbf{d }\phi(\epsilon u ,\epsilon v)
\end{align*}
$$
它的物理意义是：如果某种流体以速度 $\underline \phi$ 流动，那么它绕着一个小四边形的环流是 $\underline \phi$ 绕着小四边形的积分，也是通量 2-形式 $\mathbf{d} \phi$ 作用于小四边形两边所得的值。我们知道，对一个 1-形式求外导数相当于得到某个矢量场的旋度，那么我们有：
$$
\int_{\Pi(\epsilon u ,\epsilon v)} \phi = \mathbf{d} \phi(\epsilon u ,\epsilon  v) = (\nabla  \times  \phi) \cdot \hat  n \delta \mathcal{A}
$$
如果我们选择了一般的 $u,v$ 呢？此时，2-形式的表达式变成
$$
\mathbf{d} \phi(u,v) = \nabla_{u} \phi(v) - \nabla_{v} \phi(u) - \phi([u,v])
$$
实际上，此时的平行四边形不再封闭，为了使得其封闭，我们必须额外补上一条短边积分 $\Omega$ 在这条短边上额外获得了贡献。（之前在定义黎曼曲率张量时，我们已讨论过这一点！）
![[Pasted image 20240824201050.png|500]]

接着我们可以看一下 2-形式的外导数。设 $\Pi(\epsilon u ,\epsilon v ,\epsilon w)$ 是按照右手定则形成的小平行六面体的表面，我们考虑一个 2-形式 $\Psi$ 在有向二维边界 $\Pi$ 上的积分：
$$
\Omega (\epsilon u ,\epsilon v ,\epsilon  w) = \iint_{\Pi} \Psi 
$$
根据我们之前的定义，显然我们要做的是将 2-形式 $\Psi$ 应用到一个一个小面元上，在将所得的值累加起来，用经典微积分的语言来说，就是：
$$
\Omega(\Pi) = \iint_{\Pi} \underline\Psi  \cdot  \hat n d \mathcal{A}
$$
![[Pasted image 20240824201821.png]]
从如图所示的几何直观中很容易知道：从左、右这一对端面流出的流量是 $[\partial_{1} \Psi^{1}] \mathcal{V}$，因此，从这个“盒子”内流出的总流量自然是
$$
[\partial_{1} \Psi ^{1} +\partial_{2} \Psi ^{2} + \partial_{3} \Psi ^{3}]\mathcal{V} = (\nabla \cdot \underline \Psi )\mathcal{V}
$$
这显然是 $\Psi$ 的外导数！

## $(\star)$ 外微积分的基本定理：广义斯托克斯定理
我们接下来介绍本节中最重要的定理。我们会先应用它得到经典微积分中的一些重要结论，再给出证明。设我们有一个 $p+1$ 维的定向紧区域 $R$，将其 $p$ 维边界记为 $\partial R$，$\phi$ 是一个 $p$ -形式，那么我们有：
$$
\int_{R} \mathbf{d} \phi = \int_{\partial  R} \phi  
$$

我们先举出一些人畜无害的小例子吧。现在给出 $\mathbb{R}^{2}$ 中的区域 $R$，设其面积为 $\mathcal{A}(R)$，我们考虑 1-形式 $x \mathbf{d}y$ 顺时针绕其边界的积分。
![[Pasted image 20240824202736.png]]
从经典微积分的角度，我们可以被夹在高度 $(y,y + \delta y)$ 之间的一条微元，点在运动过程中会先划过右侧，再划过左侧。因此，点划过这个条带的两侧时带来的贡献是：
$$
(x \mathbf{d} y ) (\delta  r_{1}) + (x \mathbf{d}y)(\delta r_{2}) = (x_{1} -  x_{2}) \delta y = \delta \mathcal{A}
$$
因此积分的结果应该是这个区域的面积。这可以通过外微分基本定理一眼看出来：
$$
\oint_{\partial  R} x \mathbf{d} y = \iint_{R} \mathbf{d}(x \mathbf{d}y) = \iint_{R}  \mathbf{d}x \wedge  \mathbf{d}y = \mathcal{A}(R )
$$


我们现在看一下 $\mathbf{d}^{2} \Phi = 0$ 的含义，使用两次基本定理：
$$
0 = \int_{R}  \mathbf{d}^{2} \Phi = \int_{\partial R} \mathbf{d} \Phi = \int _{\partial(\partial R)} \Phi 
$$
这里的 $\Phi,R$ 都是任意的，因此这个结果似乎从几何上告诉我们：边界的边界是 0. 这可以通过下图这个平行六面体的例子来理解：每条边界被正向走过一次，又反向走过一次：
![[Pasted image 20240824203948.png]]

接下来，我们要说明外微积分基本定理包含了所有经典向量微积分的定理。首先取 $\Phi = f$ 为 0-形式，那么 $\mathbf{d} \Phi = \mathbf{d}f$ 是 1-形式，$R$ 是一维的曲线 $K$，而 $\partial R$ 则是曲线 $K$ 的端点。因此此时我们有：
$$
\int_{k }\mathbf{d}f = f(b) - f(a) \Rightarrow  \int_{K} (\nabla f) \cdot dr  = f(b) - f(a)
$$
这是经典微积分中的牛顿-莱布尼兹公式。

再取 $\Phi = \phi$ 为 1-形式，则 $\mathbf{d} \Phi$ 为向量场 $\nabla \times \underline \phi$ 对应的通量 2-形式，$R$ 是二维可定向曲面，$\partial R$ 是其一维边界。将 1-形式写为：
$$
\phi = \phi_{x} \mathbf{d}x + \phi_{y} \mathbf{d}y \Rightarrow  \mathbf{d} \phi = (\partial_{x} \phi_{y} - \partial_{y} \phi_{x} )\mathcal{A}
$$
那么可以写出：
$$
\oint_{\partial  R} \phi_{x} dx + \phi_{y} dy = \iint_{R}(\partial_{x} \phi_{y} - \partial_{y} \phi_{x})dxdy
$$
这是格林公式。对于更加一般的情况，我们将其推广到空间中，取 $R$ 为三维空间中的二维曲面，我们就得到了：
$$
\oint_{\partial R} \underline \phi \cdot dr = \oint_{\partial R} \phi = \iint_{R} \mathbf{d} \phi = \iint_{R}  (\nabla \times \underline \phi )\cdot  \hat n  \cdot d \mathcal{A}
$$
这是所谓斯托克斯公式。
最后，如果我们将 $\Phi= \Psi$ 取为 2-形式，$\mathbf{d}\Psi = (\nabla \cdot  \underline\Psi )\mathcal{V}$ 。那么此时的 $R$ 是一个有向体积 $V$，边界 $\partial R$ 是一个二维可定向曲面。于是我们就得到了所谓的高斯公式：
$$
\iint_{R}(\nabla \cdot  \underline \Psi )d \mathcal{V} = \iint_{\partial R} \underline \Psi  \cdot \hat n \cdot  d \mathcal{A}
$$

现在，我们将针对二维的特殊情形证明外微积分基本定理。
![[Pasted image 20240824210048.png]]
如图，很容易发现：假如我们有一个 1-形式，那么下式成立：
$$
\oint_{\partial R} \phi = \sum_{R\text{内部的单元格}} \oint_{\partial(\text{单元格})} \phi = \sum_{R\text{内部的单元格}}  \mathbf{d}\phi(\epsilon u , \epsilon v)  \Rightarrow   \oint_{\partial R} = \iint_{R}  \mathbf{d} \phi 
$$
这样我们就完成了这个特殊情形下的证明。这种手段在数学分析中被用于证明格林公式、斯托克斯定理和高斯定理。

之前我们说过，一个解析的复变函数满足：
$$
\mathbf{d}(f \mathbf{d}z) = 0
$$
那么我们可以立刻得到解析函数满足的柯西定理：
$$
\oint_{\partial R} f \mathbf{d}z = \iint_{R}  \mathbf{d}(f \mathbf{d}z) = 0
$$
就算我们研究的函数不是解析的，这种方法也可以用于计算某些积分的值，例如取 $f (z) = \bar z$：
$$
\oint_{\partial R} \bar z \mathbf{d}z = \iint_{R} \mathbf{d}(\bar z \mathbf{d}z) =2 i \iint_{R} \mathcal{A} = 2i \mathcal{A}(R)
$$

除此之外，我们还可以得到所谓庞加莱引理。这里我们只处理一个简单的情形，即 1-形式的庞加莱引理。设 $\phi$ 在 $\mathbb{R}^{n}$ 的单连通区域上是闭的，我们要证明 $\phi$ 也是恰当的。我们构造势能：
$$
f(p) = \int_{o}^{p} \phi
$$
其中 $o$ 是势能零点。如图，设 $p_{1}, p_{2}$ 是临近的两个点，连接它们的短向量是 $\epsilon v$，那么两点间的势能差是
$$\delta f = \mathbf{d} f (\epsilon v) = \int_{- K_{1} + K_{2} }\phi = \int_{\epsilon v} \phi = \phi(\epsilon v)$$
从而我们就得到了 $\phi = \mathbf{d} f$。
![[Pasted image 20240824212006.png]]


## 德拉姆上同调简介
前面的庞加莱引理指出：在单连通区域上，一个微分形式是闭的等价于它是恰当的。但若区域 $R$ 不是单连通的，那么这一结论基于不成立。在非单连通区域上，研究那些是闭的但是不是恰当的微分形式可以得到关于 $R$ 的详细拓扑信息。

我们首先从闭的但不是恰当的 1-形式开始，构建德拉姆上同调群 $H^{1}(R)$。为此，我们关注一个特殊的二维涡旋向量场。
![[Pasted image 20240824214402.png]]
在 $\mathbb{R}^{2}$ 的极坐标系下，考虑以原点为中心的逆时针涡旋，其流速为：
$$
|\underline \phi| = \dfrac{q}{2 \pi  r}
$$
我们将长度为 $r$ 的半径向量旋转 $\dfrac{\pi}{2}$ 后得到对应的涡流的方向向量。为了使得涡旋 1-形式沿着圆周的积分与半径无关，我们选择涡旋 1-形式为：
$$
\phi = \dfrac{q}{2 \pi r^{2}} [- y \mathbf{d}x + x \mathbf{d}y] 
$$
此时有：
$$
\mathcal{C} = \oint_{K_{r}}\phi = q
$$
这说明 $\phi$ 绝对不可能是恰当的，然而我们却能证明它是闭的：
$$
\begin{align*}
\left(\dfrac{2\pi }{q}\right) \mathbf{d} \phi &= - \dfrac{1}{r^{4}}(\mathbf{d}r^{2}) \wedge  [- y \mathbf{d}x +  x \mathbf{d}y] + 2 \dfrac{1}{r^{2}} \mathbf{d}x \wedge \mathbf{d}y\\
&= - \dfrac{1}{r^{4}}2(x \mathbf{d}x + y \mathbf{d}y) \wedge  [- y \mathbf{d}x +  x \mathbf{d}y]  + 2 \dfrac{1}{r^{2}} \mathbf{d}x \wedge \mathbf{d}y \\
&= - \dfrac{1}{r^{4}}2(x^{2} + y^{2}) \mathbf{d}x \wedge \mathbf{d}y + 2 \dfrac{1}{r^{2}} \mathbf{d}x \wedge \mathbf{d}y\\
&= 0
\end{align*}
$$
我们可以来看看涡旋 1-形式的几何意义：
![[Pasted image 20240824220657.png]]
从图中可以明显看出：
$$
\dfrac{1}{2}( - y \delta x + x \delta  y) = \delta \mathcal{A} = \dfrac{1}{2} r(r \delta  \theta)
$$
于是我们有：
$$
\phi = \dfrac{q}{2 \pi } \mathbf{d} \theta  \Rightarrow  \mathbf{d} \phi = \dfrac{q}{2 \pi  } \mathbf{d}^{2} \theta  = 0 
$$
这就怪了！我们目前明明处在单连通区域上啊！解决这个问题的方式相当微妙 ： 这是由于 $\theta$ 的多值性—— 对于给定的一个点，$\theta$ 可以有无数多个值，因此，$\theta$ 甚至不是坐标的函数！我们可以在 $S$ 上定义一个单值角函数，这时确实有:
$$
\oint_{L} \dfrac{q}{2 \pi } \mathbf{d} \theta  = 0
$$
![[Pasted image 20240824221331.png]]
（其实这个例子还有一个很简单的解释，虽然 $\mathbb{R}^{2}$ 是单连通的，但是 $\mathbb{R}^{2} - \text{原点}$ 却不是单连通的，一个回路无法穿过原点，连续变形，直至收缩到一点。）但是，如果我们在有孔的平面上这样做，我们将立刻遇到麻烦—— $\theta$ 不是连续的，更不是可微的！

我们之前看到 $\mathcal{C}= \oint_{K_{r}} \phi$ 与 $K_{r}$ 的大小无关，这实际可以被进一步推广：如果我们将圆周逐渐变形成任意的形状，只要在变形过程中不跨过任何奇点（这里当然就是原点啦），积分的值都不会改变。换言之，在包含涡旋奇点的回路上，闭 1-形式都有相同的环量 $q$，而在不包含奇点的会路上环量为 $0$。注意：这个结论不止对我们刚刚构造的涡旋 1-形式有用，它对于任何闭 1-形式都是有用的！我们可以将其换一种表述方法：在环路连续变形的情况下，一个闭 1-形式沿着环路的环量（称为“德拉姆周期”）是不变的。考虑到这个环量只与环路围绕的奇点有关，因此我们可以认为每个奇点拥有一个内禀的属性，这个属性就是我们所说的“留数”。

现在我们回到所谓第一德拉姆上同调群 $H^{1}(\mathbb{R}^{2} -\text{原点})$，群中的元素是 1-形式的等价类：如果两个 1-形式在绕所有环路时具有相同的环量，则我们认为它们之间存在等价关系。用术语来说，我们称这两个 1-形式是上同调的。
显然，如果两个 1-形式 $\tilde \phi$ 和 $\phi$ 是等价的，这意味着：
$$
\exists f , \tilde \phi - \phi = \mathbf{d}f
$$
每个等价类（称为“上同调类”）都按照环量 $\mathcal{C}$（称为上同调类的“周期”）来定义。显然，如果我们取该群的两个不同元素相加，必然有：
$$
\mathcal{C}(\phi_{1} + \phi_{2}) = \mathcal{C}(\phi_{1}) + \mathcal{C}(\phi_{2})
$$
因此，我们可以说群 $H^{1}(\mathbb{R}^{2} - \text{原点})$ 同构于实周期加法群 $\mathbb{R}$。

接下来可以考虑 $\mathbb{R}^{3}$ 中的 1-形式。注意到 $\mathbb{R}^{3}  -\text{原点}$ 是单连通的（即使从 $\mathbb{R}^{3}$ 中挖去原点，我们仍然能将一个回路连续地收缩到一点），因此 $\mathbb{R}^{3}  -\text{原点}$ 中的闭 1-形式也是恰当 1-形式。而 $\mathbb{R}^{3}  -z\text{轴}$ 的情况则与 $\mathbb{R}^{2} -\text{原点}$ 的情况类似。

接下来我们要讨论与 $2$ -形式相关的第二德拉姆上同调群，我们先定义一个在 $\mathbb{R}^{3}$ 中有奇点的向量场，令：
$$
\hat r = \dfrac{1}{r} \vec r     \quad r = \sqrt{x^{2} + y^{2} + z^{2}}
$$
我们要定义的向量场是：
$$
\underline \Psi = \dfrac{q}{4 \pi } \dfrac{ \hat  r}{ r^{2}}
$$
这可以看作流体以匀速被泵入原点的流速场，也可以被看作点电荷的电场或者质点的引力场。我们可以先考虑与这个向量场相关的 1-形式：
$$
\psi = \dfrac{q}{4 \pi  r^{3} } (x \mathbf{d}x + y \mathbf{d} y + z \mathbf{d}z)
$$
此时，沿着环路的积分就是引力或静电力做功！那么显然有 $\mathcal{W}_{J}= \int_{J} \Psi  = 0$，因此 $\Psi$ 是闭的，又容易证明 $\Psi$ 是恰当的，对应的 0-形式势能：
$$
f =  - \dfrac{q}{4 \pi  r}
$$
这验证了我们对 $\mathbb{R}^{3}  -\text{原点}$ 区域上 $H^{1}(R)$ 的研究——没有什么特殊的。

接着我们开始研究与这个矢量场相关的通量 2-形式：
$$
\Psi = \dfrac{q}{4 \pi }  \dfrac{1}{r^{3}} (x \mathbf{d} y \wedge  \mathbf{d}z + y \mathbf{d}z \wedge \mathbf{d}x + z \mathbf{d}x \wedge \mathbf{d}y)
$$
由于：
$$
\Omega = \iint_{S}\Psi = q
$$
$\Psi$ 显然不是恰当的，但是我们可以证明它是闭的：
$$
\begin{align*}
\left(\dfrac{4\pi }{q}\right)\mathbf{d} \Psi  &= \dfrac{3}{r^{3}} \mathcal{V} - \dfrac{3}{r^{4}} \mathbf{d}r \wedge(x \mathbf{d}y \wedge\bf d z + y \mathbf{d}z \wedge \mathbf{d}x + z \mathbf{d}x \wedge \mathbf{d}y)\\
&= \dfrac{3}{r^{3}}[\mathcal{V} - \dfrac{1}{r^{2}}(x^{2}+ y^{2} +z^{2})\mathcal{V}]\\
&= 0
\end{align*}
$$
![[Pasted image 20240824224837.png]]
如图，很容易证明：在曲面连续变性的情况下，一个闭 2-形式从二维闭曲面流出的通量（称为“周期”）是不变的。这样，$H^{2}(\mathbb{R}^{3} - \text{原点})$ 也与 $\mathbb{R}$ 同构。

最后，我们来看环面上的第一上同调群。
![[Pasted image 20240824225101.png]]
如图，我们在环面上放置两种流 $\underline \lambda, \underline \sigma$，假设两种流都是闭的，它们的流线 $L_{1},L_{2}$ 显然在拓扑上不等价。另外，$\lambda,\sigma$ 都是不恰当的，这是因为：
$$
\omega_{1}(\lambda) = \int_{L_{1}}\lambda \not = 0 ,\ \omega_{2}(\lambda) = \int_{L_{2}}\lambda  = 0  \omega_{1}(\sigma) = \int_{L_{1}}\sigma  = 0 ,\ \omega_{2}(\sigma) = \int_{L_{1}}\sigma\not = 0
$$
现在考虑一个更一般的向量场 $\phi = a \lambda  + b \sigma$，显然它是闭的，但不是恰当的，而且它有两个独立的周期 $\omega_{1}(\phi), \omega_{2}(\phi)$。环面上闭 1-形式的等价类正是由这两个独立的拓扑周期确定！容易发现，$H^{1}(\text{环面})$ 是同构于 $\mathbb{R}^{2}$ 的。

因此，德拉姆上同调群用于研究非单连通区域中的闭 $p$ -形式来获得这个区域拓扑结构的信息。其中装的是 $p$ -形式的等价类。


