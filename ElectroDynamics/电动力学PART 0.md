#ElectroDynamics 

## 矢量的基本运算
我们会定义矢量的四种基本运算：加法、数乘、点乘、叉乘。这里唯一需要注意的是矢量叉乘不遵守交换律，$A \times B = - B \times A$。矢量叉乘的实际计算方法是：
$$
A \times B  = 
\begin{vmatrix} \hat x & \hat y &  \hat z \\ A_{x}& A_{y} & A_{z} \\ B_{x}& B_{y} & B_{z} \end{vmatrix}
$$

我们介绍两种三重积。首先是标量三重积，它的几何意义是三个矢量作为三条棱形成的平行六面体的体积。它的性质包括：
- 轮换对称性： $A\cdot (B \times C) = B \cdot (C \times A) = C \cdot (A \times B)$
-  交换字母顺序，得到相反的结果：$A \cdot (B \times C) = - C \cdot (B \times A)$
- 点乘和叉乘是可以互换位置的：$A \cdot (B \times C) = (A \times B )\cdot C$

矢量三重积则是由三个叉乘组成的。它具有重要性质：
$$
A \times (B \times C) = B (A \cdot C) - C(A \cdot B)
$$
注意：$A \times (B \times C)$ 和 $(A \times B) \times C$ 是两个完全不同的矢量！利用矢量三重积的相关结论，我们可以将一个式子中化简到至多包含一个叉乘。

我们在电动力学里面通常会遇到电荷被放置在 $r'$ 点处，而我们希望研究 $r$ 点的情况。这个时候我们将从源点 $r'$ 指向场点 $r$ 的的矢量称作 Separation Vector，这里使用 $\mathscr{r}$ 表示。


## 矢量微积分
首先我们介绍标量场的**梯度**。假定我们有标量场 $T(x,y,z)$，我们可以这样来写出它的全微分：
$$
dT = \left(\dfrac{\partial T }{\partial x} \hat x + \dfrac{\partial T}{\partial y}\hat y + \dfrac{\partial T}{\partial z}\hat z\right)\cdot (dx \hat x + dy \hat y  + dz \hat z ) = (\nabla T) \cdot(dl)
$$
这里的 $\nabla T$ 就是标量场 $T$ 的梯度。几何意义上，梯度的方向是标量场上升最快的方向，梯度的大小就是这个方向上标量场的“斜率”。梯度为 0 的点就被称为是标量场的“驻点”。

我们把 $\nabla T$ 称为 Del Operator。它不是一个通常的矢量，但是可以作用在通常的标量函数或者矢量场上，表示一种“求梯度”的操作。刚才我们已经把它作用在了标量函数上，下面我们将其作用在矢量场上。

假定我们有矢量场 $v$，那么我们如下定义**散度**：
$$
\nabla \cdot v  = \dfrac{\partial v_{x}}{\partial x} + \dfrac{\partial v_{y}}{\partial y} + \dfrac{\partial v_{z}}{\partial z}
$$
散度衡量矢量场的“源与汇”。

我们将 $\nabla \times v$ 称为矢量场的**旋度**，它衡量矢量场在某点附近的“旋转”行为。

在这一部分中，我们会遭遇大量的矢量求导恒等式。在本笔记中，我们不一一列出。我们可以来看一下标量场、矢量场的二阶导数。我们知道，矢量场的散度是个标量场，因此我们可以对它再求梯度；标量场的梯度和矢量场的旋度都得到一个矢量场，因此我们可以对其再求散度和旋度，这样我们就会得到二阶导数。
首先，最简单的是：
$$
\nabla \cdot (\nabla T) = \nabla^{2}T = \dfrac{\partial ^{2}T}{\partial x^{2}} + \dfrac{\partial ^{2}T}{\partial y^{2}}  + \dfrac{\partial ^{2}T}{\partial z^{2}} 
$$
我们可以将 $\nabla^{2}$ 叫做拉普拉斯算子。
两个最为重要的结论是：梯度的旋度为 0
$$
\nabla \times (\nabla T) = 0 
$$
旋度的散度为 0：
$$
\nabla \cdot (\nabla \times T) = 0
$$
我们也可以计算旋度的旋度，尽管这实际上无法带来任何新的东西：
$$
\nabla \times (\nabla \times v) = \nabla \cdot (\nabla \cdot v) - \nabla^{2}v 
$$
散度的梯度 $\nabla (\nabla \cdot v)$ 也无法为我们带来任何新的东西。


我们介绍我们在这门课程中经常遇到的三种积分。如果空间中存在矢量场 $v$，那么我们将线积分表达为：$\int_{a}^{b} v \cdot dl$；对于闭合回路上的线积分，我们将其表达为 $\oint v \cdot dl$。线积分的一个重要例子是计算力 $F$ 所作之功。线积分的结果通常与路径有关，如果它与路径无关，那么我们就说矢量场是保守的。
我们将面积分表达为 $\int_{S} v \cdot da$。如果曲面 $S$ 闭合，我们可以将面积分写为 $\oint v \cdot da$。其中 $da$ 的方向规定实际上是任意的，但是，对于闭合曲面来说，我们通常将“指向曲面外”规定为 $da$ 的方向。面积分通常被用于计算通量。面积分的结果通常与我们选择的曲面有关，但是，在特定条件下，它可能只与曲面的边界有关。
最后我们介绍体积分。假定空间中存在标量场 $T$ ，那么体积分表达为 $\int T d \tau$。有的时候我们也会对矢量场进行体积分，如果单位矢量都是常数，我们可以将单位矢量直接提出，例如：
$$
\int v d \tau = \int (v_{x} \hat x + v_{y}\hat y + v_{z}  \hat z) d \tau  = \hat x \int v_{x} d \tau + \hat y \int v_{y} d \tau + \hat z \int v_{z}d \tau 
$$


我们知道，在一元函数微积分中，我们有微积分基本定理（牛顿-莱布尼兹公式）：
$$
\int_{a}^{b} \left(\dfrac{\mathrm{d}f}{\mathrm{d}x}\right) dx = f(b) - f(a)
$$
它的几何意义是我们在 $(a,b)$ 之间不断累加函数的小变化 $df$，然后我们就可以得到 $a,b$ 两点处函数值的差。微积分基本定理可以被推广到矢量场中。注意：在前面我们提过，标、矢量场的微分运算有三种：梯度、散度、旋度，每一种微分运算都对应一个定理。
首先我们考虑将基本定理推广到梯度这种求导运算上。我们已经知道，假如空间中存在标量场 $T$，我们在空间中移动一个微小的位移 $d l_{1}$，那么标量场值的变化是 $(\nabla T) \cdot dl_{1}$。类比上面的微积分基本定理，我们就容易得到：
$$
\int_{a}^{b} (\nabla T) \cdot dl  = T(b) - T(a)
$$
注意到这个式子的左侧和路径有关，但是右侧和路径无关，那么我们可以立刻得到推论：$\int_{a}^{b} (\nabla T) \cdot dl$ 与路径无关，且显然 $\oint (\nabla T)\cdot dl=0$ 
矢量场散度的基本定理是：
$$
\int_{V} (\nabla \cdot v) d \tau = \oint_{S} v \cdot da
$$
这个公式被称作“格林公式”、“高斯公式”或者“散度定理”。这个定理如同微积分基本定理一样，它说明了在一个区域内矢量场的散度的积分完全由它边界上的面积分来确定（对于基本定理来说，$a,b$ 就是边界。）至于其物理意义，我们可以使用不可压缩的流体来解释：假设曲面内有很多点在释放不可压缩流体，那么这些流体必然会通过曲面穿出去。因此我们只要在边界上计算通量，就可以得到“产生流体的速率”，也就是散度。
矢量场旋度的基本定理：
$$
\int_{S} (\nabla \times v) \cdot da = \oint_{P} v \cdot dl 
$$
也就是说，一个矢量场的散度在一个曲面上的积分，等于这个矢量场沿着曲面边缘的线积分。直观上来说，曲面上一个矢量场的散度是在衡量这个矢量场有多少“漩涡”，这可以通过沿着矢量场走一圈，计算矢量场的环量 $\oint_{P} v \cdot dl$ 来等效地得到。通过这个定理，我们可以立刻得到推论：$\int (\nabla  \times v)\cdot da$ 只与所选曲面的边界有关，而与曲面的形状无关。对于闭合曲面来说，$\oint (\nabla  \times v )\cdot da = 0$，这是因为它的边界已经收缩为一点。

最后我们介绍分部积分，这已经在分析学中学过，也就是：
$$
\int_{a}^{b} f \left(\dfrac{\mathrm{d}g}{\mathrm{d}x}\right) dx = - \int_{a}^{b} g \left(\dfrac{\mathrm{d}f}{\mathrm{d}x}\right) + fg |_{a}^{b}
$$


## 曲面坐标系
在之前，我们都使用笛卡尔直角系来表示坐标，现在，我们希望使用一些其他坐标系。例如，球坐标系使用极径、极角（从 $z$ 轴转过的角度）、方位角（从 $x$ 轴转过的角度）来。很容易从几何关系上直接看出笛卡尔坐标和球坐标的转换：
$$
x = r \sin \theta \cos \phi   \quad y = r \sin \theta \sin \phi \quad z  = \cos \phi
$$
在球坐标里面，我们显然也可以找到三个单位矢量：$\hat r, \hat \theta, \hat \phi$，那么一个矢量显然可以表示为 $A = A_{r} \hat r + A_{\theta} \hat \theta + A_{\phi} \hat \phi$，但是注意，这个时候和直角坐标系不同的一点是 $\hat r,\hat \theta, \hat \phi$ 三个单位矢量都是变化的。容易注意到极坐标的线元是 $dl = dr \hat r + r d \theta \hat \theta + r \sin \theta d \phi \hat \phi$ ，体积元是 $d\tau^{2} = r^{2}\sin \theta dr d \theta d \phi$
我们可以推导极坐标下的梯度、散度、旋度。例如，我们需要推导梯度：
$$
\nabla T  = \dfrac{\partial T}{\partial x}\hat x + \dfrac{\partial T}{\partial y} \hat y + \dfrac{\partial T}{\partial z}\hat z
$$
在极坐标下的表示方法。注意到此时 $T = T(r,\theta,\phi)$，那么我们需要推导：
$$
\dfrac{\partial T}{\partial x} = \dfrac{\partial T}{\partial r} \left(\dfrac{\partial r}{\partial x}\right)+ \dfrac{\partial T}{\partial \theta} \left(\dfrac{\partial \theta}{\partial x}\right) + \dfrac{\partial T}{\partial \phi} \left(\dfrac{\partial \phi}{\partial x}\right)
$$
这样推导完成之后，我们需要再将 $\hat x$ 使用 $\hat r,\hat \theta ,\hat \phi$ 表示，这样我们就推出了极坐标下的梯度算子。散度和旋度算子的推导过程是类似的，我们可以在课本的首页找到。

还有一种曲线坐标是柱坐标。它和直角坐标的变换关系是：
$$
x = s \cos \theta \quad y = s \sin \theta  \quad z = z 
$$

## Delta 函数
我们考虑一个在当前定义下的悖论。假定我们有矢量场 $v = \dfrac{1}{r^{2}}\hat r$，那么经过计算我们可以知道它的散度是处处为 0 的，但是，对于任意包围原点的面，该矢量场的通量不为 0，这二者显然是相互矛盾的。注意到 $\int (\nabla \cdot v) d \tau$ 的结果实际上与 $r$ 无关，那么根据散度定理，我们可以发现这个矢量场就像只在原点处有散度一样。（这就像是一个质点一样，在某一点处的密度是无穷大，其余位置密度都为 0，总质量为一个有限值。）在这种情况下，我们会引入一个广义函数——狄拉克 Delta 函数来解决这个问题。在一维上，Delta 函数被定义为：
$$
\delta(x) = \begin{cases}
0  &\quad x \not= 0 \\
+\infty &\quad  x =0  
\end{cases}
\quad 
\int_{-\infty}^{+\infty} \delta(x)dx = 1
$$
你可以把 Delta 函数想成面积为 1 的，不断变窄的矩形或者等腰三角形。容易注意到 Delta 函数满足性质 $f (x) \delta (x) = f (0) \delta(x)$，那么可以很容易发现选择性质：
$$
\int_{- \infty}^{+ \infty} f(x) \delta (x-a)dx = f(a)
$$
还容易注意到 Delta 函数的一个性质是
$$
\delta(kx) = \dfrac{1}{|k|} \delta(x)
$$
对于这个结果的直观理解，我们可以视为 $\delta(kx)$ 是在 $x$ 方向上“压缩”了 Delta 函数。

虽然 Delta 函数并不是一个符合数学上对“函数”的定义的函数，但是 Delta 函数在积分号下面可以正常地运行，甚至你可以理解为 Delta 函数是只能在积分号下面运行的。一般来说，$D_{1}(x),D_{2}(x)$ 是含有 Delta 函数的表达式，如果它们两个相等，我们的意思是它们对于任意函数有着相同的“选择”作用，也就是：
$$
\int_{-\infty}^{+\infty} f(x) D_{1}(x) dx = \int_{-\infty}^{+\infty} f(x) D_{2}(x) dx
$$

一个三维的 Delta 函数被定义为：
$$
\delta^{3}(r) = \delta(x)\delta(y) \delta(z)
$$
它在全空间的积分：
$$
\int_{\text{all space}} \delta^{3}(r) d\tau = \int_{-\infty}^{+\infty}\int_{-\infty}^{+\infty}\int_{-\infty}^{+\infty} \delta(x) \delta(y)\delta(z) dxdydz = 1
$$
从而它也有选择性质：
$$
\int_{\text{all space}}  f(r) \delta^{3}(r-a)d\tau = f(a)
$$

那么我们可以解决在本节一开始时提出的问题，我们需要使用 Delta 函数来定义散度：
$$
\nabla \left(\dfrac{\hat r }{r^{2}}\right) = 4 \pi \delta^{3}(r) 
$$
这个时候就不会出现不自洽的问题。显然我们也可以得到：
$$
\nabla^{2} \dfrac{1}{r} = -4 \pi \delta^{3}(r)
$$

## 亥姆霍兹定理
我们知道，麦克斯韦方程组是一个关于矢量的导数（散度、旋度的）方程组，那么假使我们讨论一个矢量场 $F$，它的散度由一个标量场 $D$ 决定，其旋度由一个矢量场 $C$ 决定，也就是：
$$
\nabla \cdot F = D \quad  \nabla \times F=  C
$$
凭借这些散度和旋度信息，我们能够唯一地确定矢量场 $F$ 吗？在一般情况下，这是不行的。但是，在我们现在所讨论的电动力学中，我们会选择特殊的边界条件（例如，我们通常选择的是无穷远处的电场和磁场为 0），在这个情况下，亥姆霍兹定理保证我们可以仅仅使用 $D, C$ 来确定 $F$。


我们接下来讨论几个特殊的矢量场。首先考虑 $\nabla \times F=0$ 的情况，我们知道梯度的旋度为 0，因此，此时 $F$ 被写为某种**标量势的梯度** ：
$$
F = - \nabla V
$$
此时，$F$ 显然有性质：
- 对于任意位置都有 $\nabla \times F = 0$
- $\int_{a}^{b}F\cdot dl$ 与路径无关，$\oint F \cdot dl = 0$

再考虑 $\nabla \cdot F = 0$ 的情况，我们知道旋度的散度为 0，因此，此时 $F$ 被写为某种**矢量势的旋度**：
$$
F = \nabla  \times A
$$
此时，$F$ 显然具有性质：
- 对于任意位置都有 $\nabla \cdot F=0$
- $\int F \cdot da$ 只与所取区域的边界有关，且在闭合区域上为 0

在一般的情况下，我们需要将以上两个情况叠加起来。此时矢量场 $F$ 被写成：
$$
F = \nabla \times A - \nabla V
$$
右边的项就是矢量场 $F$ 的势。
