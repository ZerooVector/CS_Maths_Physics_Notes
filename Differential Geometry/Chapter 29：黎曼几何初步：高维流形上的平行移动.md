#DifferentialGeometry 

在研究三维空间中的二维曲面时，我们使用角盈定义曲率:
$$
\mathcal{K}(p) = \lim_{\Delta  \rightarrow p} \dfrac{\mathcal{E}(\Delta)}{\mathcal{A}(\Delta)}
$$
但是对于 $n$ 维流形来说，角盈显然是笨拙的。要定义曲率，我们必须首先理解 $n$ 维流形上的平行移动。与二维曲面上的高斯曲率不同，在 $n$ 维流形上，曲率有 $\dfrac{1}{12}n^{2}(n^{2}-1)$ 个分量，这些分量需要使用黎曼张量表示。黎曼曲率的平均称为里奇曲率张量。此外，一件重要的事情是，我们需要将和乐性、雅可比方程从二维曲面推广到 $n$ 维流形上。为了形象化地做这些事情，我们会可视化三维流形，在三维流形上足以介绍不同于二维流形的各种新特性。

## $n$ 维流形上的角盈
在之前的所有研究中，将二维流形嵌入到三维空间中都是一种行之有效的方法，但是这个方法显然无法持续下去：我们无法可视化一个四维空间，将三维流形嵌入到四维空间中对我们的研究没有丝毫作用。因此，接下来我们只关注流形的内蕴几何性质。在三维流形中，我们显然可以选择无数个不同的平面来构建测地线三角形，每个平面都有自己的法向量，并且对应一个曲率（这个曲率称为截面曲率）。如图，三个正交平面的截面曲率是独立的（注意：我们现在研究的是内蕴几何，我们这里提到的截出的“平面”在外在几何中看来都是三维空间中二维曲面，因此它们的曲率显然不一定为零）：
![[Pasted image 20240818172346.png|400]]
注意：此时的黎曼张量有六个分量，然而我们只得到了三个角盈。在四维流形的情况下这会变得更糟。因此，此时角盈只能部分反映曲率，为了找到所有曲率分量，我们必须转向和乐性。

## $(\star)$ $n$ 维流形上的平行移动：三种构造方法

### 构造 1：定角圆锥上的最近向量
回顾二维曲面上平行移动的重要性质：假如一个向量 $w$ 沿着曲线平行移动（不失一般性，我们设这条曲线就是测地线 $G$，其余情况使用测地线分段逼近即可），只需保持平行移动后的向量 $w_{\parallel}$ 与 $G$ 的夹角不变即可，但是这在三维的情况下遇到困难：
![[Pasted image 20240818173054.png]]
平行移动的结果应该是锥面的哪一条母线？我们可以通过 $\mathbb{R}^{3}$ 中的特殊结果来想一想。显然，合理的做法是：$w_{\parallel}(p \rightarrow q)$ 是 $\mathcal{C}$ 的母线中端点离 $w(p)$ 端点最近的一条。

### 构造 2：平行移动一整个平面
实际上，我们提出了这些构造方法，是因为"测地线与平行移动的向量夹角不变"这一约束已经不能使得我们唯一确定平行移动后的向量了。我们先考虑沿着 $\mathbb{R}^{3}$ 中的欧几里得直线 $G$ 移动向量 $w_{p}$。设 $w_{p}$ 与 $G$ 的切向量 $v$ 的夹角为 $\alpha$，它们张成的平面为 $\Pi(p)$。将 $\Pi(p)$ 沿着 $G$ 平行移动得到 $\Pi_{\parallel}$，最后，取 $\Pi_{\parallel}$ 上与 $v$ 夹角为 $\alpha$ 的单位向量为 $w(p)$ 平行移动后的向量即可。
![[Pasted image 20240818194947.png]]
如图，在一般的三位流形上，操作方法是类似的。我们从 $p$ 点向 $w(p)$ 和 $v(p)$ 的线性组合的所有方向发射测地线，从而获得一个二维子流形 $\Pi(p)$。根据构造方法，$q$ 和 $q$ 附近的点必然包含在 $\Pi(p)$ 中。于是，我们可以在 $\Pi(p)$ 上找到 $q$ 点附近的小区域，并向这个小区域上的所有方向发射测地线，这样我们就将 $\Pi(p)$ 这个二维流形整体平行移动到了 $\Pi(p \rightarrow q)$。之后，在平行移动矢量 $w(p)$ 时，除了保持其与 $G$ 的夹角不变之外，应当使得它与 $\pi(p \rightarrow q)$ 相切。重复这个过程，我们就完成了平行移动。

### 构造 3：希尔德的梯子
![[Pasted image 20240818200613.png]]

## $(\star)$ 协变导数
之前我们研究过 $\mathbb{R}^{3}$ 中的方向导数和二维流形中的协变导数，二者的关系是：
$$
D_{v}w = \mathcal{P}[\nabla_{v}w] = \nabla_{v} ww - (n \cdot \nabla_{v}w) \cdot n 
$$
这是协变导数的外在表达，因此也无法使用。我们考虑之前提过的内在表达：将向量从点 $q$ 平行移动回点 $p$，得到 $w_{\parallel}(q \rightarrow p)$，使用 $\dfrac{w_{\parallel}(q \rightarrow p)  - w(p)}{\epsilon}$ 求出协变导数。类似地，在 $n$ 维流形上的协变导数也是这样定义：
$$
\nabla_{v} w = \dfrac{w_{\parallel} (q \rightarrow p) - w(p)}{\epsilon}
$$
或者：
$$
w_{\parallel}(q \rightarrow p)  - w(p)  = \epsilon \nabla_{v} w  = \nabla_{\epsilon v}w
$$
显然根据这个定义我们有：
$$
\nabla_{v} w_{\parallel}  = 0 
$$
如果 $v$ 是测地线的速度向量，那么沿着自身的平行移动就是它自己，也就是说，测地线（微分）方程是这样的：
$$
\nabla_{v} v   = 0 
$$

## $(\star)$ 黎曼曲率张量
### 绕着小平行四边形的平行移动
在研究二维流形时，我们将一个向量沿着某个回路做平行移动，从而引入了和乐性的概念，现在我们来重新做这一点。我们找到单位向量场 $u,v$，如图，先在 $o$ 点放置平行四边形的两条边 $v (o) \delta v, u (o)\delta u$；再如图放置（平行移动后）的 $v (a)\delta v$ 和 $u (p)\delta u$。一般来说，这样制作的平行四边形并不是闭合的，但是这里我们先假装能找到一种方式让它闭合，从而我们可以沿着回路 $oabqpo$ 平行移动一个向量。
![[Pasted image 20240818204202.png]]
如图，我们仍然将和乐性算子定义为 $w$ 返回 $o$ 点时和从 $o$ 点出发时的差，而且，在二维曲面上我们已经知道和乐性正比于曲率。在这里介绍的三维流形中，平行移动的结果与向量 $w$ 有关（在二维流形中，所有向量"刚性地"一同进行平行移动），因此，我们引入与回路有关的和乐性算子，将其作用在矢量 $w$ 上以得到和乐性：
$$
- \delta w_{\parallel}   = \mathcal{R}(u \delta u  , v \delta v )w
$$

### 将四边形封闭起来
我们定义两个向量的对易子/李括号（尽管书上将其叫做"换位子"）为：
$$
[v,u] = \nabla_{v} u - \nabla_{u} v 
$$
很容易看出对易子是反对称的。如图，从几何意义上可以看出，用来补全平行四边形的向量就是：
$$
c = [v \delta v , u  \delta u ] = [v,u] \delta u \delta  v
$$
![[Pasted image 20240818210316.png|550]]

### $(\star \star \star)$ 黎曼曲率的一般公式
之前我们证明 GCB 时，曾经引入开曲线 $K$ 的和乐性，也就是找到一个基准向量场 $U$ ，然后 $\mathcal{R}_{U}(K) = \delta_{K}(\angle U w_{\parallel})$。我们仍然先从二维流形开始，直接将 $U$ 取为 $w$，并考虑它在短向量 $\epsilon$ 上的和乐性，此时的和乐性显然可以和协变导数联系在一起（当然，我们将 $U$ 的模长取为 1）：
$$
- \mathcal{R}_{U}(\epsilon) = \delta_{\epsilon}(\angle U_{\parallel}) = |\nabla_{\epsilon}U|
$$
![[Pasted image 20240818211426.png]]
对于 $n$ 维流形的一般情况，我们也可以类似处理。选取 $w_{o}= w(o)$，那么我们有：
$$
- \delta_{oa} w_{\parallel}  = w(a) -  w_{\parallel}  = \nabla_{u \delta  u }w(o) = \delta u \nabla_{u}  w(o)
$$
显然，当我们考虑整条回路的时候，和乐性与基准向量场无关，那么我们现在直接计算整条回路上的和乐性：
$$
\begin{align*}
-\delta w_{\parallel} &= - [\delta_{oa} + \delta_{ab}  + \delta_{bq}  + \delta_{qp}  + \delta_{pa} ] w_{\parallel}\\
&= \delta v [\nabla_{v}w(a) -\nabla_{v}w(o)] - \delta u [\nabla_{u}w(p) - \nabla_{u} w(o)] + \delta u  \delta v \nabla_{[u,v]}w(o)\\
&= \delta v [\delta u \nabla_{u}  \nabla_{v} w(o)] - \delta u [\delta v\nabla_{v} \nabla_{u} w(o)]  - \delta  u  \delta v  \nabla_{[u,v] }w(o)\\
&= \delta u  \delta v [\nabla_{u} \nabla_{v} - \nabla_{v} \nabla_{u}   - \nabla_{[u,v]}] w(o)\\
&= \delta u  \delta v \mathcal{R}(u,v) w(o)
\end{align*}
$$
那么我们就可以看出之前引入的黎曼曲率算子是（它作用在一个向量 $w$ 上，得到该向量沿着 $u,v$ 生成的回路平行移动得到的和乐性）：
$$
\mathcal{R}(u,v) = [\nabla_{u},\nabla_{v}] - \nabla_{[u,v]}
$$
它显然是反对称的。我们立刻给出黎曼曲率张量的标准定义：
$$
\mathbf{R}(u,v;w) = \mathcal{R} (u,v) w 
$$

### 黎曼曲率确实是个张量
我们现在来解释 $\mathcal{R}$ 确实是个张量——我们要求张量满足以下两条性质：
- 输出线性地依赖于每一个输入
- 输出只依赖于在求值点的输入向量。
看第三项：第一个性质可以由协变导数的线性性保证。验证第二个性质：假设我们令 $w^{NEW} = f w^{OLD}$，且 $f(o)=1$，此时直接计算可以证明：
$$
\mathbf{R}(u,v;w^{OLD})  = \mathbf{R}(u,v;w^{NEW})
$$
从几何上可以看出这一点，我们只是改变了基准向量场，这对于沿着整个回路的平行移动没有任何影响。
对于前两项，第二个性质由取极限的情况可以证明（回路收缩到 $o$ 点），线性性仍然可以使用几何关系或者计算得到。

### ($\star$)黎曼张量的分量
为了给出某个几何对象的数值描述，我们会在 $n$ 维流形每个点的切空间内引入一组标准正交向量 $\{e_{i}\}$ 作为基底。这样，每一点切空间内的矢量可以表示为 $u = u^{i}e_{i}$。利用黎曼曲率张量的线性性，它可以被写为：
$$
\mathbf{R}(u,v,w) = \mathbf{R}(u^{i}e_{i}, v^{j}e_{j}; w^{k} e_{k}) = \mathbf{R}(e_{i},e_{j};e_{k}) u^{i} v^{j} w^{k}
$$
我们定义黎曼张量的分量为它作用在三个基底上得到的系数：
$$
\mathbf{R}(e_{i},e_{j}; e_{k}) = R_{ijk}^{l} e_{l} 
$$
为了后面使用方便，我们定义符号：
$$
R_{ijkm}  = \mathbf{R}(e_{i},e_{j};e_{k}) \cdot e_{m}
$$
由于我们选择了正交基，因此有：
$$
R_{ijkm}= R_{ijk}^{m}
$$

### 回路的和乐性只依赖于所在平面和面积
我们知道，对于二维流形，回路的和乐性只依赖于面积，与形状无关。现在，由于平面有很多，我们需要考虑特定的 $\Pi(u,v)$，即由 $u$ 和 $v$ 张成的平面。现有结论：若绕平面 $\Pi(u,v)$ 上最终面积为 0 的小平行四边形平行移动 $w_{o}$，那么相连点和乐性正比于小平行四边形的面积 $\delta A$，但是与其形状无关。
证明：将生成回路的两个向量记为 $u\delta u = \delta u^{i}e_{i}, v \delta v  = \delta v^{i} e_{i}$，那么回路所围的面积是：
$$
\delta \mathcal{A} = \delta u^{1} \delta v^{2} - \delta u^{2}  \delta  v^{1}
$$
设初始的向量 $w_{o} = w_{o}^{k}e_{k}$，和乐性 $\delta w_{\parallel}= \delta w_{\parallel}^{l}e_{l}$，那么：
$$
\begin{align*}
\delta w_{\parallel} &= - \delta w_{\parallel}^{l} e_{l}\\
&= \delta  u^{i}  \delta  v^{j}   w_{0}^{k} R_{ijk}^{l} e_{l} \\
&= \delta  \mathcal{A}[R_{12k}^{l} w_{o}^{k}] e_{l}
\end{align*}
$$
其中最后一步的推导中使用了黎曼张量的反对称性。

### ($\star$)黎曼张量的对称性
我们考虑以下三维流形上的黎曼张量的分量 $R_{ijkm}$，在它的 81 个分量中，真正互相独立的只有六个。首先考虑之前已经见鬼哦的反对称性：
$$
R_{ijkm} = - R_{jikm}
$$
这会使得它的分量数目从 81 减少到 27，现在我们要证明另一个对称性：
$$
R_{ijmk} = - R_{ijkm}
$$
证明很简单。容易注意到 $\delta _{\parallel}$ 与 $w_{o}$ 应当正交，那么：
$$
\delta w_{\parallel} \cdot w_{o} = 0 \Rightarrow  [\mathcal{R}(u,v) w_{o}] \cdot  w_{o}  = 0
$$
现在设 $x,y$ 是任意向量，并令 $w_{o}= x+y$，我们又可以得到：
$$
[\mathcal{R}(u,v)x]\cdot y = - [\mathcal{R}(u,v) y]\cdot x
$$
我们直接给出黎曼张量剩下的三个对称性，这些结论可以使用后面微分形式的语言简单地证明：
- 对于前三个向量循环排列的对称性：$R_{ijkm} + R_{jkim} + R_{kijm} = 0$
- 对于两对矢量交换的对称性：$R_{ijkm} = R_{kmij}$
- 微分比安基恒等式：$\nabla_{x} \mathcal{R}(u, v) w + \nabla_{u} \mathcal{R}(v, x) w + \nabla_{v}\mathcal{R}(x, u) w = 0$（这对爱因斯坦的引力理论是至关重要的）

### 截面曲率
我们现在希望沿着平面 $\Pi(u,v)$ 内的一条曲线平行移动一个也处于 $\Pi(u,v)$ 内的矢量，但是我们遇到的困难是：即使初始矢量 $w_{o}$ 位于 $\Pi$ 平面内，它在被平行移动的过程中也会转出 $\Pi$，为此我们引入一个正交投影算子，如果 $\Pi= \Pi(e_{1},e_{2})$：
$$
\mathcal{P}[a^{1} e_{1} +a^{2}e_{2} +a^{3}e_{3}] = a^{1}e_{1} + a^{2}e_{2}
$$
我们要证明以下结论：设 $w_{o}$ 是 $\Pi$ 内的任意向量，它绕着 $\Pi$ 内的一个回路平行移动生成 $w_{\parallel}$，令 $w_{\parallel}$ 在 $\Pi$ 内的投影是 $\mathcal{P}(w_{\parallel})$，定义 $\mathcal{K}(u,v)$ 为单位面积的小回路上 $\mathcal{P}(w_{\parallel})$ 的旋转，则 $\mathcal{K}(u,v)$ 与 $w_{o}$ 的选择无关，因此 $\mathcal{K}(u,v)$ 被称为截面 $\Pi$ 的截面曲率。
证明方法是直接计算：
$$
-\begin{bmatrix}\delta w_{\parallel}^{1} \\ \delta w_{\parallel}^{2} \end{bmatrix} = \begin{bmatrix}R_{1211}w_{o}^{1}  + R_{1221}w_{o}^{2} \\  R_{1212} w_{o}^{1} + R_{1222} w_{o}^{2}\end{bmatrix} \delta \mathcal{A}
$$
利用黎曼张量的反对称性有：
$$
R_{1211}= R_{1222}=  0 \quad R_{1221} = - R_{1212} 
$$
那么我们就得到了截面曲率的定义：
$$
\mathcal{K}(\Pi) = \mathcal{K}(e_{1},e_{2}) = [\mathcal{R}(e_{1},e_{2})e_{2}]\cdot e_{1} = R_{1221}
$$
也就是说，它是 $e_{2}$ 的在 $e_{1},e_{2}$ 生成的回路上的和乐性在 $e_{1}$ 上的投影。因此我们有：
$$
\mathcal{P}[\delta w_{\parallel}] = \begin{bmatrix}\delta w^{1}_{\parallel}   \\  \delta  w^{2}_{\parallel}\end{bmatrix}  = \begin{bmatrix}-w_{o}^{2}  \\  w_{o}^{1}\end{bmatrix} \mathcal{K}(\Pi) \delta \mathcal{A} = w_{\perp} \mathcal{P}(\Pi)\delta A
$$
这里的 $w_{\perp}$ 就是将 $w$ 逆时针旋转 90 度。
因此，我们回到了最初的观点：曲率是二维流形内单位面积上的和乐性！
另外，知道了黎曼张量，我们自然就知道了所有二维平面的截面曲率，但是如果知道了所有的截面曲率，实际上我们可以重建黎曼张量。

>在介绍黎曼曲率的这一部分的最后，我们要说明：这部分研究是黎曼当年在高斯的“逼迫”下完成的（作为黎曼入职时的演讲）。由于当时根本没有平行移动这一工具（这是 Levi-Civita 提出的），因此黎曼并不是根据我们上面的这条路径给出了黎曼曲率张量。他的发现来源于对黎曼几何中的度规和欧氏几何中度规的偏差的计量。另外，黎曼在其私人笔记中已经发现了上文中提到的微分比安基恒等式，这个恒等式将成为广义相对论的基石！

## $n$ 维流形上的雅可比方程

### 截面上的雅可比方程
根据“曲率”这个概念的推广，我们很容易知道应如何将雅可比防尘也推广到 $n$ 维流形中。显然，原来的曲率应该替换成截面曲率，这里的截面是由速度向量 $v$ 和从两个质点之间的连接测地向量 $\xi$ 形成的。这个平面上的截面曲率大小就决定了截面上两条测地线之间的相对加速度。回顾一下前面这张图：
![[Pasted image 20240819142757.png]]
现在我们在一个二维平面 $\Pi= \Pi(v,\xi)$ 内做类似操作，依然得到：
$$
\delta v_{\parallel} = \delta  t \nabla_{v}  \nabla_{v} \xi
$$
这里的 $\delta v_{\parallel}$ 是正交于 $v$ 的，如果在二维的情况下，它必然处在平面 $\Pi$ 内，而现在 $\delta v_{\parallel}$ 由 $\Pi$ 内的分量（改变 $\Pi$ 内两条测地线之间的距离）和与 $\Pi$ 正交的分量（没用）组成。将上面的结论用 $\nabla_{v}  \nabla_{v} \xi$ 在 $\Pi$ 内的投影上，并利用 $\delta t \rightarrow 0$ 时的几何关系，得到：
$$
\delta t  \mathcal{P}[\nabla_{v} \nabla_{v} \xi] = \mathcal{P}[\delta v_{\parallel}] = v_{\perp} \mathcal{K}(\Pi) \delta \mathcal{A}= \left[ - \dfrac{\xi}{|\xi|}\right]\mathcal{K }(\Pi) |\xi | \delta t 
$$
也就是说：
$$
\mathcal{P}[\nabla_{v}  \nabla_{v} \xi] =  -\mathcal{K}(\Pi)\xi
$$
这被称为截面雅可比方程

### 截面雅可比方程的几何意义
下面的三张图给出了截面雅可比方程的几何意义：
![[Pasted image 20240819151112.png]]

### 一般雅可比方程的计算证明
现在，我们在平面 $\Pi$ 上构建正交基，取 $e_{1} = \dfrac{\xi}{|\xi|}, e_{2} = v$，那么 $\Pi$ 的单位法向量是 $e_{1} \times e_{2}$。截面曲率定义为：
$$
\mathcal{K}(\Pi) = R_{1221} = [\mathcal{R}(e_{1},e_{2})e_{2}]\cdot e_{1}  = [\mathcal{R}(\hat \xi , v)v]\cdot \hat \xi
$$
再考虑一件事：之前在 $\delta t  \rightarrow  0$ 时，$v \delta t$ 和 $\xi$ 都是沿着测地线方向的。那么，无论是 $v$ 沿着 $\xi$ 平行移动还是 $\xi$ 沿着 $v \delta t$ 平行移动，二者的夹角都是不变的，这意味着由 $v,\xi$ 生成的平行四边形是闭合的，回顾我们之前的讨论，这意味着：
$$
[v,\xi] = 0 \Rightarrow  \nabla_{v} \xi  =\nabla_{\xi} v  
$$
这意味着我们能对黎曼曲率算子做些简化：
$$
\mathcal{R}(v,\xi ) = [\nabla_{v} , \nabla_{\xi}]
$$
从而我们直接计算：
$$
\begin{align*}
\nabla_{v}  \nabla_{v}  \xi &= \nabla_{v}  \nabla_{\xi}  v \\
&= [\nabla_{v}  , \nabla_{\xi}] v + \nabla_{\xi}  (\nabla_{v} v)\\
&= \mathcal{R}(v,\xi ) v + \nabla_{\xi}(0)
\end{align*}
$$
这样我们会得到一般形式的雅可比方程：
$$
\nabla_{v}\nabla_{v} = - \mathcal{R}(\xi ,v)v
$$
如果要将其恢复到截面雅可比方程的形式，只需将右侧写成分量式：
$$
\mathcal{R}(\xi ,v) v = \mathcal{K}(\Pi)\xi + R_{1223} |\xi | e_{3}
$$
再在两侧使用投影算子即可。


## 里奇张量
看看上面描写雅可比方程的几何意义的图，当质点被正值的截面曲率拉向中心，黑色圆盘的面积 $\delta \mathcal{A}$ 明显收缩，我们现在希望研究这个圆盘面积收缩的规律。首先考虑 $\Pi$ 绕着中心质点的轨迹旋转的时候，所有截面的截面曲率由相同的正值 $\mathcal{K}$，那么我们有：
$$
\dot{(\delta \mathcal{A})} (0) = 2 \pi r(0) \dot r(0) = 0
$$
以及：
$$
\ddot{(\delta \mathcal{A})}(0) = 2\pi[\dot r^{2}(0) + r(0)_{}\ddot r(0)]   = - 2 \mathcal{K}\delta \mathcal{A}(0)
$$
从而从泰勒展开可以看出，对于很小的 $t$ 有：
$$
\delta \mathcal{A}(t) - \delta \mathcal{A}(0) = - \mathcal{K} \delta \mathcal{A}(0) t^{2}
$$
但是实际上，$\mathcal{K}= \mathcal{K}(\theta)$，容易看出此时有（此时，这些质点其实已经不一定共面，我们是在把一个个小三角形的面积加起来）：
$$
\delta \mathcal{A}(t) - \delta \mathcal{A}(0) = - \overline{\mathcal{K}} \delta \mathcal{A}(0) t^{2}
$$
其中平均截面曲率是：
$$
\overline{\mathcal{K}} = \dfrac{1}{2\pi} \int_{0}^{2\pi} \mathcal{K}(\theta)d \theta
$$
我们考虑如何用黎曼曲率张量表示 $\mathcal{K}(\theta)$，根据下图，直接计算可得：
![[Pasted image 20240819155250.png]]
$$
\begin{align*}
\mathcal{K}(\theta) &= [\mathbf{R}(ce_{1} + se_{2},v ; v)] \cdot (ce_{1} + se_{2})\\
&= c^{2} \mathcal{K}(0) + s^{2} \mathcal{K}\left(\dfrac{\pi}{2}\right) +2sc R_{1332}
\end{align*}
$$
从而直接得到：
$$
\overline{\mathcal{K}} = \dfrac{\mathcal{K}(0) + \mathcal{K}\left(\dfrac{\pi}{2}\right)}{2}
$$
由零点的任意性得到：$\overline{\mathcal{K}}$ 实际上是任意两个方向截面曲率的平均值，我们进一步改写：
$$
\begin{align*}
\mathcal{K}(0) + \mathcal{K}\left(\dfrac{\pi}{2}\right) &= \mathbf{R}(e_{1},e_{3} ; e_{3})\cdot e_{1} + \mathbf{R}(e_{2},e_{3};e_{3}) \cdot e_{2} \\
&= R_{1331}+R_{2332}+R_{3333}\\
&= R_{m33}^{m}
\end{align*}
$$
我们现在定义里奇曲率张量：
$$
\mathbf{Ricci}(v,w) = \sum_{m} \mathbf{R}(e_{m},v;w)\cdot e_{m}   
$$
或者写成：
$$
\mathbf{Ricci}_{jk}  = \mathbf{R}_{mjk}^{m}
$$
容易从黎曼张量推出里奇张量确实是一个张量，另外，里奇张量有对称性：
$$
\mathbf{Ricci}(w,v) = \mathbf{Ricci}(v,w)
$$
因此我们得到之前的平均曲率：
$$
\mathcal{K}(0) + \mathcal{K}\left(\dfrac{\pi}{2}\right)   = \mathbf{R}_{m33m}  = \mathbf{Ricci}(v,v) = \mathbf{R}_{jk}v^{j} v^{k}
$$
我们就得到了关于面积的雅可比方程：
$$
\ddot{\delta \mathcal{A}} = - \mathbf{Ricci}(v,v) \delta \mathcal{A}
$$
我们直接将上面的分析推广到四维流形上，假设我们仍然发射一组到中心质点等距的质点，且这组质点初始位于与 $v$ 正交的子空间中，那么此时的“阴影部分”应该是一个小球面，包围着一个体积 $\delta \mathcal{V}$。我们不加证明地给出这个体积随时间的演化：
$$
\ddot{\delta \mathcal{V}} = - \mathbf{Ricci}(v,v) \delta \mathcal{V}
$$
这就是里奇张量，是某种意义上黎曼曲率的平均值。


第 29 集就要停止在这里了，在这一集中，我们以三维流形为例引入了很多有趣的新思想，但是这远远不够——我们都身处在四维流形中，并向着时间轴上的“未来”飞奔。在下一节中，我们将看到这一点。



