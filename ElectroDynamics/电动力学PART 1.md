#ElectroDynamics 

## 静电场

### 静电场的散度和旋度
我们现在考虑一些问题，我们有一些电荷 $q_{1}, q_{2},\cdots$，我们将这些叫做“场源电荷”，我们现在考虑它们加在一个试探电荷 $Q$ 上的力。这个问题可以使用**叠加原理**求解（注意，叠加原理不是一个逻辑上的事实，而是实验上得到的结果）。假如这些电荷是运动的，那么这个问题并不是那么好解决，我们需要考虑到电荷的速度和加速度。并且，电磁波所带的“信息”以光速传播，这些影响也要考虑。我们现在还不能解决这个问题，在这一章中，我们只解决场源电荷是固定的这一种情况。

我们首先介绍库仑定律，这是由实验保证的：
$$
F = \dfrac{1}{4 \pi \epsilon_{0}} \dfrac{qQ}{\mathscr{r}^{2}} \mathscr{\hat  r}
$$
我们定义试探电荷受到的力 $F = QE$，这里的 $E$ 被称为电场，那么根据叠加定理：
$$
E(r) = \dfrac{1}{4 \pi \epsilon_{0}} \sum_{i} \dfrac{q_{i}}{\mathscr{r}_{i}^{2}} \mathscr{\hat r}_{i}
$$
对于电荷在线上、面上、空间上分布的情形，我们只要知道 $dq = \lambda dl' = \sigma da' = \rho d\tau'$ 即可，例如，对于在空间中有分布的电荷，我们如下求出电场：
$$
E(r) = \dfrac{1}{4 \pi \epsilon_{0}} \int \dfrac{\rho(r')}{\mathscr{r}^{2}} \mathscr{ \hat r} d \tau '$$

通过一些很直观的模型，我们可以发现，穿过一个闭合曲面的电通量 $\oint E \cdot da$ 是对曲面内电荷多少的衡量，例如，我们放一个电荷在原点，我们发现任意包围原点的球面上穿出的通量都是 $\dfrac{q}{\epsilon_{0}}$，这就是电场高斯定理的实质。仍然是通过基于一些直观模型的推理（例如使用电场线来表示电场），我们可以发现穿过任意曲面的通量都是 $\dfrac{q}{\epsilon_{0}}$，现在假设曲面内有许多电荷，那么穿过曲面的通量是这些电荷各自产生通量的叠加：
$$
\oint E \cdot ad = \sum_{i} \left(\oint E_{i} \cdot da \right)  = \sum_{i}\left(\dfrac{1}{\epsilon_{0}}q_{i}\right)  
$$
那么这就是静电场高斯定理的数学表达：
$$
\oint E \cdot da = \dfrac{1}{ \epsilon} Q_{\text{enclosed}}
$$
**也就是说，高斯定理实际上就是通过库仑定律和叠加原理做出来的，其实并没有提供什么新东西** 注意到 $Q_{\text{enclosed}} = \int \rho d \tau$，与散度定理对比可以直接得到电磁场的散度：
$$
\nabla \cdot E = \dfrac{1}{\epsilon_{0} } \rho
$$
我们可以从前面提出的电场的计算式上验证这一结果的正确性。注意到：
$$
\nabla \cdot E = \dfrac{1}{4 \pi \epsilon_{0}} \int 4 \pi \delta^{3}(r - r') \rho(r') d\tau' = \dfrac{1}{\epsilon_{0}} \rho(r)
$$
注意这里的积分实际上是取遍所有的源点 $r'$，Delta 函数的筛选性质只选出了 $r = r'$ 处的值。
高斯定理可以用于求解有强对称性的静电场，主要包括球对称、柱对称和平面对称的情况。运用高斯定律和叠加原理可以让我们灵活地求解电场。

电场力是一个有心力，我们很容易知道任意的有心力都是保守力。对于点电荷产生的场，我们很容易计算得到：
$$
\int_{a}^{b} E \cdot dl = - \dfrac{1}{4 \pi \epsilon_{0}} (\dfrac{q}{r_{b}} - \dfrac{q}{r_{a}})
$$
那么根据旋度定理，容易知道：
$$
\oint E \cdot dl = 0 \Rightarrow \nabla \times E = 0 
$$
根据电场的叠加原理，我们很容易证明任何静电场的散度都为 0.

### 静电场的势与能量
在上一节中，我们提到过，静电场是无旋的。这个特性可以让我们化简许多有关静电场的问题。其中，最重要的化简手段就是将电场写为某个标量的梯度。我们首先来证明这一点。
我们之前已经提到过，$\int E \cdot dl$ 这个积分仅仅与积分的起止点有关而与路径无关。因此我们将 $\mathcal{O}$ 定为某个参考点，定义一个函数由从 $\mathcal{O}$ 到 $r$ 的积分决定，这个函数被称为电势：
$$
V(r) = - \int_{\mathcal{O}}^{r} E \cdot dl 
$$
注意到两点间的电势差：
$$
V(b) - V(a) = - \int_{a}^{b} E \cdot dl  = \int_{a}^{b} (\nabla V) \cdot dl  
$$
那么显然就有：
$$
E = - \nabla V
$$

我们可以对于这个定义做出一些讨论。例如：
- 为什么一个标量函数就可以包含电场的三个分量的信息？这是因为电场的旋度为 0，从而自然地提供了约束。
- 电势的零点可以任意选择。在大部分问题中（只要问题中涉及的电荷没有延伸至无穷远处），我们经常自然地将无穷远处选作电势的零点。在现实生活中，不会有电荷延伸至无穷远，因此我们完全可以将无穷远处视为零点。
- 电势遵循叠加定理。

从前面电场与电势的关系以及电场的散度表达中，我们可以直接推出泊松方程：
$$
\nabla^{2}V  =   - \dfrac{\rho }{\epsilon_{0}}
$$
在没有电荷的地方，上述方程退化为 $\nabla^{2}V = 0$，这被称为拉普拉斯方程。至于
$$
\nabla \times (-  \nabla V) = 0
$$
则没有提供新的东西。因为我们已经知道梯度的散度必须为 0。

现在我们已经发现一个有趣的事实。如果我们希望计算电场，实际上先计算电势，再计算电场是更方便的。现在我们希望从电荷的分布中推导出电势的分布，我们逐步地解决这个问题。首先，假如我们将无穷远处选择为电势的零点，那么一个点电荷的电势是：
$$
V(r) = \dfrac{1}{ 4 \pi \epsilon_{0}} \dfrac{q}{\mathscr{r}}
$$
那么，对于在空间中任意分布的电荷（当然，这些电荷不能延伸至无穷远处）有：
$$
V(r) = \dfrac{1}{4 \pi \epsilon_{0}} \int \dfrac{\rho (r')}{\mathscr{r }} d \tau'
$$
这实际上是泊松方程的一个解。

在讨论完电势以后，我们希望讨论一下电场和电势在边界上的变化情况。例如，如果一个界面上有电荷面密度 $\sigma$，那么界面两侧的电场必然是不连续的。对于法向电场，我们可以使用高斯定理求解：我们只要选择一个紧贴着界面的高斯面，即可得到：
$$
E_{1,n} - E_{2,n} = \dfrac{\sigma}{\epsilon_{0}}
$$
 对于切向电场，我们只需要取一个穿越界面两侧的环，利用 $\oint E \cdot dl=0$，立刻得到：
$$
E_{1,t} = E_{2,t}
$$
将以上两式总结，我们得到：
$$
E_{1} - E_{2} = \dfrac{\sigma}{\epsilon_{0}} \hat n 
$$
利用电势差的定义式，我们很容易发现电势在界面上是连续的，但是电势的梯度一定不连续，显然有：
$$
\nabla V_{1} - \nabla V_{2} = - \dfrac{1}{\epsilon_{0}}\sigma\hat n 
$$
或者可以写成一个简单的表达方式（上式两侧点一下 $\hat n$ 即可）：
$$
\dfrac{\partial V_{1}}{\partial n} - \dfrac{\partial V_{2}}{\partial n} = - \dfrac{1}{\epsilon_{0}}\sigma  \quad (\dfrac{\partial V}{\partial n} = \nabla V \cdot \hat n ) 
$$


首先考虑一个很简单的事实：将一个电量为 $Q$ 的点电荷从 a 点移动到 b 点，需要做多少功。显然是：
$$
W = - Q \int_{a}^{b} E \cdot dl = Q(V(b)-  V(a))
$$
那么，b、a 两点的电势差实际上是将单位电量的点电荷从 a 点搬运到 b 点需要做的功。如果将一个点电荷从无穷远处移动至 $r$ 处，需要做功 $W = QV(r)$。

我们现在考虑建立起一个离散电荷体系需要多少能量。假定我们先移动一个 $q_{1}$ 电荷到某个位置，再移动 $q_{2}$ 电荷到某个位置。那么，在移动 $q_{1}$ 的时候我们不需要付出任何的能量，但是在移动 $q_{2}$ 的时候，我们需要消耗能量 $q_{2}V_{1}(r_{2})$，也就是：
$$
W_{2} = \dfrac{1}{4 \pi \epsilon_{0}} q_{2} \left( \dfrac{q_{1}}{\mathscr{r}_{12}}\right)
$$
我们可以继续移动第 3，4，或者更多个电荷，最终我们可以计算出消耗的总能量：
$$
W = \dfrac{1}{4 \pi \epsilon_{0}} \sum_{i=1}^{n} \sum_{j > i}^{n} \dfrac{q_{i} q_{j}}{ \mathscr{r}_{ij}}
$$
在这个情况下，重复的 $(i,j)$ 对只被计算了一次，在第二个求和号上有 $j>i$ 的限制。我们现在可以改写上式，使得重复的 $(i,j)$ 对被计算两次，也就是取消第二个求和号上的限制。相应地，我们应该给上式乘以系数 $\dfrac{1}{2}$，也就是说，我们所需的总能量（系统的总电势能）为：
$$
W = \dfrac{1}{8 \pi \epsilon_{0}} \sum_{i=1}^{n} \sum_{j \not =  i}^{n} \dfrac{q_{i} q_{j}}{ \mathscr{r}_{ij}}
$$
我们将 $q_{i}$ 提出来：
$$
W = \dfrac{1}{2} \sum_{i} q_{i} \left(\sum_{i \not = j} \dfrac{1}{4 \pi \epsilon_{0}} \dfrac{q_{j}}{\mathscr{r}_{ij}}\right) \ \Rightarrow \ W = \dfrac{1}{2} \sum_{i}q_{i}V(r_{i})
$$
这就是离散的点电荷系统内储存的能量的一般计算式。

我们再考虑一个连续电荷体系。此时，上式化为：
$$
W = \dfrac{1}{2} \int \rho V d \tau 
$$
我们现在希望将上式仅仅使用 $E$ 表示。利用高斯定理：
$$
\rho = \epsilon_{0}\nabla \cdot E \ \Rightarrow \ W = \dfrac{\epsilon_{0}}{2} \int (\nabla  \cdot E) V d \tau 
$$
我们进行如下的推导，利用矢量分析公式：
$$
\nabla \cdot (VE) = V(\nabla \cdot E) + E \cdot (\nabla V)
$$
利用散度定理（这个操作就像是分部积分）：
$$
\int_{V} \nabla  \cdot (V E) \  d \tau = \oint_{S} VE\  da = \int_{V} V(\nabla \cdot E) \ d \tau + \int_{V} E \cdot(\nabla V) \ d\tau
$$
我们就得到了：
$$
W = \dfrac{\epsilon_{0}}{2} \left(\int_{S} VE \  da - \int_{V} E \cdot (\nabla V) \ d\tau  \right) = \dfrac{\epsilon_{0}}{2} \left(\int_{S} VE \  da + \int_{V} E^{2} \ d\tau  \right) 
$$
上式的积分区域本来应当是包含所有电荷的区域，但是一个更简单的方式是直接在全空间积分，此时，面积分的一项变成 0。于是，我们给出了计算连续电荷分布的系统的能量公式：
$$
W = \dfrac{\epsilon_{0}}{2} \int E^{2}\  d \tau
$$
我们仍然对这里推导出的电势做一些讨论：
- 为什么 $\sum_{i}q_{i}V_{i}$ 可能是负的，但是 $\int E^{2} d \tau$ 一定为正？这是因为第一个式子中没有考虑点电荷形成的过程，更没有计及点电荷的能量（经过计算可知，一个点电荷的内的能量实际上是无限的），我们只是将点电荷移动到一起。在写出 $\int \rho V d \tau$ 时，$r$ 处的电荷很少，它对电势的贡献为 0. 因此这里的 $V$ 是所有电荷产生的电势，而没有扣除 $r$ 处的一点点电荷。
- 我们现阶段的知识无法说明电势是储存在电场里还是电荷里。我们可以提前说明结论：这个能量储存在电场里，能量密度就是我们上文中计算得到的 $\dfrac{\epsilon_{0}}{2}E^{2}$
- 显然，能量密度正比于 $E^{2}$，那么电场能量就不满足叠加定理。

### 导体的性质
我们首先讨论理想导体的一些性质：
- 导体内的电场强度为 0。如果不为 0，导体中的载流子将不断移动，直到导体内电场强度为 0 为止。
- 导体内的电荷密度为 0。这是由高斯定理显然得到的。
- 所有电荷分布在表面。（我们暂不给出详细证明，这可以从能量极小的角度来理解。但是，注意这一般只在三维中成立。）
- 导体是等势体。
- 导体表面的电场垂直于导体，否则分布在导体表面的电荷会移动。

以上性质会导致导体附近存在电荷时，导体上出现“感应电荷”，也会导致导体存在“静电屏蔽”效应：若导体内有空腔，那么导体外的电场不会对空腔内的电场产生任何的影响。（但是，很显然的一件事情是空腔内的电荷会反映到导体表面上。）

显然，根据高斯定理和导体的以上性质，假如导体表面某处的电荷面密度为 $\sigma$，那么导体表面的电场强度为：
$$
E = \dfrac{\sigma}{\epsilon_{0}} \hat n 
$$
现在我们来考虑导体表面的电荷受到的力。这时候，我们只考虑导体表面的一个微元，我们将这个微元产生的电场记为 $E_{p}$，其余部分的电场记为 $E_{o}$，那么此处导体表面的电场为：
$$
E = E_{p}+ E_{o}
$$
作用在这一个微元上的力显然是由 $E_{o}$ 引起的，那么我们现在计算 $E_{o}$。根据高斯定理显然有：
$$
E_{1} = E_{o}+ \dfrac{\sigma}{2 \epsilon_{0}} \quad  E_{2} = E_{o} - \dfrac{\sigma}{2 \epsilon_{0}}
$$
那么我们就知道了：
$$
E_{o} = \dfrac{1}{2}(E_{1}+ E_{2})
$$
那么，单位面积上受力就是 $f = \dfrac{1}{2 \epsilon_{0}} \sigma^{2} \hat n$

最后，假设我们找到两块导体，上面分别分布 $+Q,-Q$ 的电荷。此时，若将 $Q$ 翻倍，那么空间中 $E$ 会翻倍，两块导体之间的电势差 $V$ 也会翻倍。我们将：
$$
C = \dfrac{Q}{V}
$$
定义为导体的电容。有些时候，电容器中只有一个导体，此时的另一个导体就是我们设想的无穷大球面。
为了充满一个电容，我们会将正电荷从负极移动到正极。假设某个时候正极所带的电荷为 $q$，那么要移动 $dq$ 的电荷，就需要做功 $\dfrac{q}{C}dq$。从而将电容从 $q=0$ 充电到 $q=Q$ 所需的能量可以通过积分得到：$W = \dfrac{1}{2} \dfrac{Q^{2}}{C}$，也就是 $W = \dfrac{1}{2}CV^{2}$。这就是电容器储存的能量。

### 拉普拉斯方程
静电学的基本目的是：给出空间中的电荷分布，我们希望求出空间中场的分布。这可以通过库仑定律实现，然而，这通常很难计算。因此，一种更可行的分布是先计算势。我们可以利用之前提到过的泊松方程：
$$
\nabla^{2}V = - \dfrac{1}{\epsilon_{0}}\rho 
$$
很多时候，我们其实只关系那些没有电荷分布的部分，电势（场）是怎么样的。这个时候，拉普拉斯方程退化为泊松方程：
$$
\nabla^{2}V = 0 
$$

一维下的方程非常简单：
$$
\dfrac{\mathrm{d}^{2}V}{\mathrm{d} x^{2}} = 0 
$$
其通解显然为：
$$
V(x) = mx + b 
$$

它有两条显然的性质：
- $V(x)$ 是 $V(x+a)$ 和 $V(x-a)$ 的平均值
- $V(x)$ 没有极值

对于二维拉普拉斯方程，我们有类似的性质：
$$
V(x,y) = \dfrac{1}{2\pi R} \oint_{\text{circle}} V dl 
$$
并且 $V$ 没有极大值和极小值。对于三维同样也是成立的。这可以通过简单地对一个点电荷的情况计算，再运用电势的叠加定理得到证明。

从一维的情况我们已经发现：某些适当的条件可以确定 Laplace 方程的解（例如两个端点处的电势值），而某些条件却不行（例如两个端点处电势的导数）。我们现在希望对于一般的、三维的 Laplace 方程找到定解所需的边界条件，这样的条件则被称为唯一性定理。

第一唯一性定理：Laplace 方程在区域 $V$ 上的解由其边界上的电势唯一确定。这容易证明：假设区域内可以有两套电势 $V_{1}$ 和 $V_{2}$，记它们的差值是 $V_{3}$，那么 $V_{3}$ 显然满足 Laplace 方程，且 $V_{3}$ 在边界上为 0，由于 $V_{3}$ 无极大值、极小值的性质，它只能在区域 $V$ 上全为零。得证。这个定理显然可以被推广到：区域 $V$ 内的电势仅由区域 $V$ 内部的电荷和边界上的电势唯一确定。

第二唯一性定理：若区域 $V$ 中有导体，每个导体上的电荷总量已知，区域内的电荷密度 $\rho$ 已知，则电势被唯一确定。这个证明稍难：
设有两个电场满足所述条件，由高斯定理：
$$
\nabla \cdot E_{1} = \dfrac{1}{\epsilon_{0}} \rho  \qquad \nabla \cdot E_{2} = \dfrac{1}{\epsilon_{0}} \rho 
$$
我们可以对每个导体的外表面使用高斯定理：
$$
\oint E_{1} \cdot dS = \dfrac{1}{\epsilon_{0}}Q_{i}   \qquad \oint E_{2} \cdot dS = \dfrac{1}{\epsilon_{0}}Q_{i}
$$
同理，对于外表面（可至无穷远处）也能写出上式。现在，我们检查两个场的差值，它显然满足：
$$
\nabla \cdot  E_{3}= 0 \qquad \oint E_{3} \cdot dS = 0
$$
其中第二个积分是对任意表面成立的。

现在我们知道，对于每个导体的表面，其电势 $V_{3}$ 是一个常数。因此使用一个 trick：
$$
\nabla \cdot(V_{3}E_{3}) = V_{3} (\nabla \cdot E_{3}) + E_{3} \cdot (\nabla  V_{3}) = - (E_{3})^{2}
$$
另外，我们有：
$$
\int \nabla\cdot(V_{3}E_{3}) d\tau  = - \int(E_{3})^{2} d \tau  = \oint_{S}V_{3}E_{3} \cdot da 
$$
这里的 $S$ 是取遍所有表面的。而我们知道，在任意一个表面上都有 $\oint E_{3}\cdot da = 0$，那么我们立刻有：
$$
\int (E_{3})^{2} d\tau = 0 
$$
从而得证。（这个定理的证明，我认为更多是数学技巧，将 $E_{3}$ 的面积分为 0 转换为 $E_{3}^{2}$ 的体积分为 0 ）.

### 镜像法、分离变量法
镜像法里面可能有坑的一点就是在计算电势能的地方。注意不要使用原电荷和镜像电荷组成的体系直接计算电势能，否则可能差出一个常数倍。

分离变量法的想法很简单：我们希望将电势拆成几项相乘的形式，每一项只与一个坐标有关。通过这种方式，我们通常可以得到 Laplace 方程的一组解，其中的每一个解都不符合边界条件，但我们期望它们的线性组合符合边界条件（由于 Laplace 方程是线性的，所以我们可以这样做）

在直角坐标系下的分离变量非常简单，但是在球坐标系下（假设问题与 $\phi$ 无关），我们会得到两个常微分方程，其中，关于 $R$ 的可以被简单地求解：
$$
\dfrac{\mathrm{d}}{\mathrm{d}r} \left(r \dfrac{\mathrm{d}R}{\mathrm{d}r}\right) = l (l+1) R  \Rightarrow R(r) = Ar^{l} + \dfrac{B }{r^{l+1}}
$$
但是另一个关于 $\Theta$ 的方程：
$$
\dfrac{\mathrm{d}}{\mathrm{d} \theta} \left(\sin \theta  \dfrac{\mathrm{d}\Theta}{\mathrm{d}\theta}\right)= - l(l+1) \sin \theta \cdot\Theta 
$$
却不好求解。它的解是勒让德多项式：
$$
\Theta(\theta) = P_{l} (\cos\theta)  \quad P_{l}(x) = \dfrac{1}{2^{l} l!} \left( \dfrac{\mathrm{d}}{\mathrm{d}x} \right)^{l} (x^{2} - 1)^{l}  
$$
另外，这个关于 $\Theta$ 的方程显然应该有两个通解（因为它是二阶的），但是勒让德多项式只提供了一个通解。我们直接说明另一个通解会在 $\theta = 0, \theta = \dfrac{\pi}{2}$ 处爆掉，所以我们是不管另一个通解的。一个例子是 $\Theta (\theta) = \ln \left(\tan \dfrac{\pi}{2}\right)$ 。
注意：勒让德多项式仍然是一组完备且正交的多项式，因此我们可以使用求 Fourier 级数类似的技巧来计算系数。但是我们通常很难处理勒让德多项式的积分，因此对于一般的情况，我们可以将答案"猜出来"。

### 多极展开
有时候，我们希望估计我们的电荷体系在远场下产生的电场和电势，在最粗糙的近似下，我们显然可以使用点电荷来估计，其电势衰减速度是 $\dfrac{1}{r}$；再更加粗糙的情况下，我们则可以使用电偶极子，它的电势衰减速度是 $\dfrac{1}{r^{2}}$，因此，在远场条件下，它产生的影响远远小于点电荷。我们可以无限地这样做下去，从而不断获得更精确的近似。我们考虑一个通用的情形：电势是：
$$
V(r) = \dfrac{1}{4 \pi \epsilon_{0}} \int \dfrac{1}{\mathscr{r}} \rho(r') dr'
$$
这里 $r$ 是场点，而 $r'$ 是源点。使用余弦定理计算场点到源点的距离：
$$
\mathscr{r}^{2} = r^{2} + (r')^{2} - 2 r r' \cos \alpha = r^{2} \left[ 1 + \left(\dfrac{r'}{r}\right)^{2} - 2 \left(\dfrac{r'}{r}\right)\cos  \alpha   \right]
$$
或者说，$\mathscr{r} = r \sqrt{1 + \epsilon}$，而 $\epsilon = \left(\dfrac{r'}{r}\right)\left(\dfrac{r'}{r} - 2 \cos \alpha\right)$，我们可以将 $\dfrac{1}{\mathscr{r}}$ 展开，展开并整理的结果是：
$$
\dfrac{1}{\mathscr{r}} = \dfrac{1}{r} \sum_{n = 0 }^{\infty}  \left(\dfrac{r'}{r}\right)^{n} P_{n}(\cos  \alpha)
$$
回代，我们就可以得到电势的表达式。

具体来看一下：最主要的贡献项是
$$
V_{0}(r) = \dfrac{1}{4 \pi  \epsilon_{0}} \dfrac{Q}{r}
$$
第二项则是：
$$
V_{1}(r) = \dfrac{1}{4 \pi  \epsilon_{0}} \dfrac{p \cdot r}{r^{2}}
$$
其中
$$
p = \int r' \rho(r') d \tau '
$$
像是 $\rho$ 的一阶矩。因此这一项被称为"电偶极矩"。对于一系列的点电荷，电偶极矩可以写为：
$$
p = \sum q_{i}r_{i}'
$$

显然，$Q$ 不会随着坐标原点的变化而变化；但是，（计算可知）如果 $Q  \not  = 0$，那么电偶极矩 $p$ 是会随着坐标原点变化的！容易计算得到电偶极子的电场是：
$$
E(r , \theta) = \dfrac{p}{4 \pi \epsilon_{0}r^{3}} (2  \cos \theta  \hat r  +  \sin \theta \hat \theta)
$$


## 静磁场

### 洛伦兹力
我们显然需要通过场与物质的相互作用来得知场的存在，对于磁场：
$$
F = Q(v \times B)
$$
容易立刻推导得到，作用在导线上的安培力是：
$$
F = I \int dl \times B
$$

当电流流过一个面的时候，我们需要使用"面电流密度"来描述它，这定义为在垂直于电流方向的单位长度上流过的电流，也可以写为：
$$
K = \sigma v
$$
对于三维的情形也是类似的。电流密度是 $J = \rho v$。

那么，考虑一个体积 $V$，其边界为 $S$。显然有：
$$
\oint_{S}J \cdot da = \int_{V}(\nabla  \cdot J) d \tau
$$
由于电荷守恒，我们立刻得到：
$$
\nabla  \cdot J  = - \dfrac{\partial \rho}{\partial t}
$$
这被称为连续性方程。

### 毕奥-萨伐尔定律，磁场的散度和旋度
在静电场中，最简单的情形是研究一个点电荷，再使用叠加原理推广到一般的情况。而在静磁场中，我们最简单的研究对象是稳恒电流。稳恒电流产生的磁场由毕奥-萨伐尔定律给出：
$$
B(r) = \dfrac{\mu_{0}I}{4 \pi } \int  \dfrac{dl' \times \mathscr{ \hat  r}}{\mathscr{r}^{2}}
$$
这个积分是沿着电流线的方向积分的，其中 $dl'$ 是电流线微元。同理，对于二维和三维的情形可做推广。

我们可以发现：以一条直导线为中心画一个圈，沿着圈积分得到：
$$
\oint B \cdot dl = \mu_{0}I
$$
这个结果与圈的半径无关。实际上，这不必是个圈。注意到 $B = \dfrac{\mu_{0}I}{2 \pi s}\hat \phi$ 和 $dl = ds \hat  s + s  d \phi  \hat \phi + dz \hat z$，立刻可以知道：
$$
\oint B \cdot dl   = \mu_{0}I 
$$
现在假设我们有一束导线，显然就会有：
$$
\oint B  \cdot dl  = \mu_{0} I_{enc} = \int J \cdot da
$$
这个结论也被称之为安培环路定理。使用一步斯托克斯公式，我们就可以将其写成：
$$
\nabla \times B = \mu_{0}J
$$


现在我们正式计算磁场的散度和旋度。根据三维空间中的毕奥-萨伐尔定律：
$$
B(r) = \dfrac{\mu_{0}}{4 \pi} \int  \dfrac{J(r') \times \mathscr{\hat r}}{\mathscr{r}^{2}} d \tau  '
$$
将散度算子作用在右边一项上：
$$
\nabla \cdot \left(J  \times  \dfrac{\scr{\hat r}}{\mathscr{r}^{2}}\right) = \dfrac{\mathscr{\hat r}}{\mathscr{r}^{2}} \cdot (\nabla \times J)  - J \cdot \left(\nabla \times  \dfrac{ \mathscr{\hat r}}{\mathscr{r}^{2}}\right)
$$
很容易发现这两项都是 $0$（注意：这里的 $J$ 是 $r'$ 的函数，然而我们的求导是关于 $r$ 的导数）。因此静磁场的散度为 0.

同样我们来求出旋度：
$$
\nabla \times \left(J \times \dfrac{ \mathscr{\hat r}}{\mathscr{r}^{2}}\right)  = J \left(\nabla  \cdot \dfrac{\mathscr{\hat r}}{\mathscr{r}^{2}}\right)- (J \cdot  \nabla ) \dfrac{\mathscr{\hat r}}{\mathscr{r}^{2}}
$$
在这里已经去除了所有包含 $\nabla  \times J$ 的项。在第一项中，我们知道 $\nabla  \cdot \dfrac{\mathscr{\hat r}}{\mathscr{r}^{2}} = 4 \pi \delta^{3}(\mathscr{r})$，因此这一项的积分是：
$$
\int J(r') \delta^{3}(r - r') d\tau' = \mu_{0}J(r)
$$
接下来我们看另一项。这里有一个技巧：我们将对 $r$ 的导数换成对 $r'$ 的导数，并且补一个负号：
$$
- (J \cdot \nabla ) \dfrac{\mathscr{\hat r}}{ \mathscr{r}^{2}} = (J \cdot \nabla' ) \dfrac{\mathscr{\hat r}}{ \mathscr{r}^{2}}
$$
继续写下去，有：
$$
(J \cdot \nabla' ) \dfrac{\mathscr{\hat r}}{ \mathscr{r}^{2}} = \nabla' \cdot \left[\dfrac{(r - r')}{\mathscr{r}^{3}} J\right] - \left(\dfrac{r - r'}{\mathscr{r}^{3}}\right)(\nabla'  \cdot J)
$$
注意到右边一项为 0（稳恒电流的定义）. 对于左边这一项积分：
$$
\int_{V} \nabla' \cdot \left[\dfrac{r - r'}{\mathscr{r}^{3}}J \right] d \tau' = \oint_{S} \left[\dfrac{r - r'}{\mathscr{r}^{3}}J \right]  d a'
$$
我们的积分是对全空间的，因此我们自然应该把 $S$ 的边界放在无穷远处。我们不妨假设无穷远处没有电流，从而这一项积分为 0. 因此，我们就得到了静磁场的旋度：
$$
\nabla \times B  = \mu_{0}J(r)
$$

### 磁矢势
由于磁场无源，我们可以将磁场写成某个矢量场 $A$ 的旋度：
$$
B = \nabla \times A
$$
我们知道，梯度场是无旋的。因此我们其实可以在磁矢势上附加任意一个标量场的梯度。梯度场是有散的，所以一种简单的方式是构造一个梯度场加到磁矢势上，将磁矢势的散度调整到 0. 此时有：
$$
\nabla  \times B = \nabla (\nabla  \cdot A) - \nabla^{2}A = \mu_{0}J(r) \Rightarrow  \nabla^{2}A = - \mu_{0}J(r)
$$
我们给出证明，以说明这确实是可行的。假设我们希望加上 $\lambda$ 的梯度：
$$
\nabla \cdot  A  = \nabla \cdot A_{0}  + \nabla^{2} \lambda
$$
仿照之前电势满足的泊松方程，我们立刻可以看出 $\lambda$ 的解是：
$$
\lambda = \dfrac{1}{4 \pi} \int \dfrac{\nabla  \cdot A_{0}}{\mathscr{r}} d\tau '
$$
在这种情况下，$\nabla^{2}A = - \mu_{0}J(r)$ 是三个泊松方程（在笛卡尔坐标系下，$x,y,z$ 方向各有一个方程）。因此我们可以直接看出它的解：
$$
A(r) = \dfrac{\mu_{0}}{4 \pi}
 \int \dfrac{J(r')}{\mathscr{r}} d \tau '$$


我们现在讨论一下磁场中的边界条件。显然，对于一个分布了电流的面，我们有：
$$
B_{1}^{n} = B_{2}^{n}
$$
所以我们主要关注平行于面的分量。利用磁场高斯定理显然得到：
$$
B_{1}^{t} - B_{2}^{t} = \mu_{0}K
$$
如果我们将磁矢势取为没有散度的情形，那么其法向分量自然是连续的。而
$$
\oint A \cdot dl = \int B \cdot da 
$$
保证了切向分量的连续。因此磁矢势在界面两侧（和电势一样）是连续的，但是，$\dfrac{\partial A}{\partial \hat n}$ 却不是连续的。



如同电场一样，磁场也可以被多极展开：
$$
A(r) = \dfrac{\mu_{0}I }{4 \pi}\sum \dfrac{1}{r^{n+1}} \oint (r')^{n}  P_{n}(\cos  \alpha) dl'
$$
注意到磁单极子的效应始终为 0，那么现在的首阶效应由磁偶极子提供：
$$
A_{dip}(r) = \dfrac{\mu_{0}I}{4 \pi r^{2}} \oint (\hat r  \cdot r') dl' = \dfrac{\mu_{0}}{r\pi} \dfrac{m \times \hat r}{r^{2}}
$$
其中 $m = I \int da = Ia$ 称为磁偶极矩。其产生的磁场是：
$$
B_{dip}(r) = \nabla  \times A = \dfrac{\mu_{0}m}{4 \pi r^{3}}(2 \cos  \theta \hat r  + \sin \theta  \hat  \theta)
$$

## 电动力学初步
### 电动势
我们考虑一个唯象模型：要使得电荷“动起来”，我们需要“推”电荷。实验中观测到，电流密度往往与这个“推力”成正比（这里所说的推力，是作用在单位电荷量上的推力）。我们将这个关系写为：
$$
J = \sigma f
$$
比例系数 $\sigma$ 被称为电导率，而其倒数则被称为电阻率。一般来说，正是电磁力“推着”电荷向前运动，而磁场力相比于电场力来说又十分的小，因此：
$$
J = \sigma(E + v  \times B)  \approx \sigma E
$$
这个式子被称为欧姆定律。它的另一个版本是 $V = IR$。在稳恒电流的情况下：
$$
\nabla \cdot E = \dfrac{1}{\sigma} \nabla \cdot J = 0 
$$
电荷密度处处为 0，所有没有被中和的电荷都分布在表面上。

为什么电荷的速度会正比于外力，而不会一直加速呢？这是因为电荷在运动过程中经常要发生碰撞。一个简单的模型是：设电荷的平均自由程为 $\lambda$，则电荷的平均速度为：
$$
\bar v  = \sqrt{\dfrac{\lambda a}{2}}
$$
但是这个模型是错误的。一个修正过的模型是：电荷本身热运动的速度极快，但是这个速度的方向是随机的，因此电荷两次碰撞中的时间间隔 $t = \dfrac{\lambda}{v_{ther}}$，其平均运动速度
$$
\bar v  = \dfrac{a \lambda }{2 v_{ther}}
$$
从而可以推出电荷的平均运动速度：
$$
J = \left( \dfrac{n f \lambda q^{2}}{2 m v_{ther}} \right)E
$$
由于电子在电阻中流动时速度恒定，动能没有增加，因此电磁力做的功完全在电阻上转化为热。由于运送单位电荷做功为 $V$，单位时间内运送电荷数目为 $I$，因此在单位时间内做的功就是：
$$
P = VI = I^{2}R
$$
这就是焦耳定律。

在一个电路中，我们有电源提供的“外力”和静电力的参与，这些力的效果由绕着电路一圈的积分决定：
$$
\epsilon = \oint f \cdot dl  = \oint f_{s} \cdot dl  
$$
这里的 $\epsilon$ 被称为电路的电动势。由于电动势的式子是 $f_{s}$ 的路径积分，因此它也可以被定义为非静电力对单位电荷做的功。

现在我们来谈论一种最重要的非静电力来源：动生电动势。这种电动势是由洛伦兹力的分量提供的，计算方法是：
$$
\epsilon = \oint f_{mag}\cdot dl  = \oint (v \times B) \cdot dl 
$$
我们来证明动生电动势的另一种写法：考虑一根导线在 $t$ 时刻围成面积 $S$，在 $t+dt$ 时刻面积增加了一点，变成 $S + dS$，那么考虑磁通量的变化：
$$
d\phi =  \int_{dS}   B \cdot da
$$
关注导线上的一点 $P$，设此处导线的速度为 $v$，电荷相对导线的速度为 $u$，电荷的速度为 $w$，那么容易看出面积变化的微元应该写成：
$$
da = ( v\times dl) dt 
$$
从而：
$$
\dfrac{\mathrm{d}\phi}{\mathrm{d}t} = \oint B \cdot( v  \times dl)
$$
由于 $w = v + u$，且 $u$ 是平行于导线的，故上式也可写成：
$$
\dfrac{\mathrm{d}\phi}{\mathrm{d}t} = \oint B \cdot( w  \times dl) = - \oint ( w \times B) \cdot dl  = - \oint f_{mag} \cdot dl
$$
因此：
$$
\epsilon = - \dfrac{d \phi}{dt}
$$
在这里，这个式子没有引入新的物理，只是作为一种计算动生电动势的简单方式出现

### 电磁感应
法拉第通过实验提出：一个变化的磁场诱导一个电场。根据他的实验结果：
$$
\epsilon=  \oint E \cdot dl  = - \dfrac{\mathrm{d}\phi}{\mathrm{d}t} = - \int \dfrac{\partial B}{\partial t} \cdot da \Rightarrow \nabla  \times E = - \dfrac{\partial B}{\partial t}
$$
这被称为法拉第电磁感应定律。与毕奥-萨伐尔定律类似，我们可以求解感生电场：
$$
E = - \dfrac{1}{4 \pi} \dfrac{\partial }{\partial t} \int \dfrac{B \times \mathscr{\hat r}}{\mathscr{r}^{2}} d\tau
$$

我们可以研究线圈之间的互感现象。假如我们有 1，2 两个线圈，在 1 线圈中通入电流 $I_{1}$，那么 2 线圈中的磁通量应该正比于 1 线圈中通过的电流：
$$
\phi_{2} = M_{21} I_{1}
$$
同理我们有：
$$
\phi_{1}= M_{12} I_{2}
$$
$M_{21}$ 和 $M_{12}$ 被称为互感系数，我们希望算一下它们之间的关系。注意到：
$$
\phi_{2} = \int B_{1} \cdot da_{2} = \int (\nabla  \times A_{1}) \cdot da_{2} = \oint A_{1}\cdot dl_{2} 
$$
将 $A_{1}$ 的表达式代入，即可得到：
$$
M_{21} = \dfrac{\mu_{0}}{4\pi} \oint  \oint  \dfrac{dl_{1} dl_{2}}{\mathscr{r}}
$$
这很容易看出 $M_{12} = M_{21}$。那么我们可以写出互感电动势：
$$
\epsilon_{2} = - M \dfrac{\mathrm{d}I_{1}}{\mathrm{d}t}
$$
一个线圈的电流变化也会引起穿过自身的磁通量的变化，因此有自感系数 $\phi = LI$ 和自感电动势 $\epsilon = - L \dfrac{\mathrm{d}I}{\mathrm{d}t}$。

现在我们从电感这个特例开始讨论磁场中储存的能量。如果我们要向电感中输入能量，那么单位时间内做的功是：
$$
\dfrac{\mathrm{d}W}{\mathrm{d}t} = - \epsilon I = LI \dfrac{\mathrm{d}I}{\mathrm{d}t}
$$
积分即可得到电感储能：
$$
W = \dfrac{1}{2} LI^{2}
$$
我们将其推广到三维空间中：
$$
W = \dfrac{1}{2} LI^{2} = \dfrac{1}{2} I  \phi = \dfrac{I}{2}\oint A \cdot dl  = \dfrac{1}{2} \oint A \cdot I dl  \rightarrow \dfrac{1}{2}\int (A  \cdot J) d \tau
$$
我们只希望式子中出现与磁场自身有关的项，因此我们消去 $J$：
$$
W = \dfrac{1}{2 \mu_{0}} \int A \cdot (\nabla \times B) d \tau
$$
由于：
$$
\nabla \cdot(A \times B) = B \cdot (\nabla \times A) - A \cdot (\nabla \times B)
$$
那么：
$$
W = \dfrac{1}{2 \mu_{0}} \left[\int B^{2} d \tau  - \int  \nabla  \cdot (A \times B) d \tau\right] = \dfrac{1}{2 \mu_{0}}\left[\int B^{2} d \tau - \oint (A  \times B)da\right]
$$
将积分区域取成无穷大，自然得到结论：
$$
W = \dfrac{1}{2 \mu_{0}} \int B^{2} d\tau
$$

### 麦克斯韦方程组
在这里，我们走向电磁学的高峰、电动力学的起始。我们已经集齐了所有电磁学的实验定律：
$$
\nabla \cdot E = \dfrac{1}{\epsilon_{0}} \rho \quad \nabla \cdot B = 0 \quad \nabla \times E = - \dfrac{\partial B}{\partial t} \quad \nabla \times B  = \mu_{0}J
$$
不幸的是，这套方程中存在一个致命的错误！我们对方程 3 两侧求散度：
$$
\nabla \cdot(\nabla \times E) = 0  \quad \dfrac{\partial }{\partial t}(\nabla \cdot B) = 0
$$
没有问题。但是现在让我们对方程 4 作用一下：
$$
\nabla \cdot(\nabla \times B) = 0 \quad  \mu_{0}(\nabla  \cdot J) = ?
$$
电流密度的散度不一定为 0，看起来安培定律对非稳恒电流的情形失效了！现在，麦克斯韦要从理论上修复这一点。我们需要使得第（4）个方程右侧为 0，那么：
$$
\nabla \cdot J  = - \dfrac{\partial \rho}{\partial t}= - \nabla (\epsilon_{0} \dfrac{\partial E}{\partial t})
$$
于是，我们将方程修正为：
$$
\nabla  \times B  = \mu_{0}J  + \mu_{0} \epsilon_{0} \dfrac{\partial E}{\partial t}
$$
我们将 $\epsilon_{0} \dfrac{\partial E}{\partial t}$ 一项称为位移电流。于是，我们给出完整版的真空中的 Maxwell 方程组：
$$
\nabla \cdot E = \dfrac{1}{\epsilon_{0}}\rho  \quad  \nabla  \cdot B = 0 \quad \nabla \times E = - \dfrac{\partial B}{\partial t} \quad \nabla \times B  = \mu_{0}J  + \mu_{0}\epsilon_{0} \dfrac{\partial E}{\partial t}
$$
如果有磁单极子，那么方程中的两条会被改写：
$$
\nabla \cdot B  = \mu_{0} \rho_{m} \quad  \nabla  \times E = - \mu_{0}J_{m}- \dfrac{\partial B}{\partial t}
$$
在讨论电介质、磁介质中的 Maxwell 方程组时，我们引入了两个辅助量：$D, H$。此外，麦克斯韦方程组还有边界条件：
$$
D_{1}^{n} - D_{2}^{n} = \sigma_{f} \quad B_{1}^{n} - B_{2}^{n} = 0 \quad E_{1}^{t} - E_{2}^{t} = 0  \quad H_{1}^{t} - H_{2}^{t} = K_{f}\times \hat n 
$$
