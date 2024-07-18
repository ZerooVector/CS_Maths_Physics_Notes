#ElectroDynamics 

## 狭义相对论简介
我们可以注意到，有许多电磁学规律都是与速度相联系的，例如洛伦兹力。在爱因斯坦之前，已经有很多人试图解释这个“速度”是相对于什么的速度。爱因斯坦基于对前人错误的分析（例如“以太”的引入），以及对于某些实验现象的观察（例如动生电动势和感生电动势的巧合），宣称：没有一个“绝对静止”的参考系，所有的速度都是相对于你目前选择的参考系而言的。于是，他提出了狭义相对论。狭义相对论的基础假设有两点，是：
- 相对性原理：物理定律在一切惯性系中都适用
- 光速不变：无论光源和观察者如何移动，观测到的真空中的光速总是不变的
很容易通过光钟实验和一些几何关系得到以下几个结论：
- 同时的相对性：在某一惯性系内同时不同地发生的两个事件，在另一惯性系内不同时
- 动钟变慢：动钟记录的时间间隔 $\Delta \bar t$ 和静钟记录的 $\Delta t$ 之间满足关系：$\Delta \bar t  = \dfrac{1}{\gamma} \Delta t, \gamma  = \dfrac{1}{\sqrt{1 - \dfrac{v^{2}}{c^{2}}}}$ 
- 动尺收缩：$\Delta \bar x  = \gamma \Delta x$
以及容易推出洛伦兹变换：
$$
\bar x = \gamma(x - vt) \quad  \bar  t =\gamma\left(t - \dfrac{v}{c^{2}}x\right)
$$
使用四维矢量可以将洛伦兹变换使用更简单的方式表达。令：
$$
x^{0} = ct ,x^{1} = x, x^{2} = y ,x^{3} = z
$$
洛伦兹变换被写为：
$$
\bar x = \begin{bmatrix}\gamma & - \gamma \beta & 0 & 0  \\  - \gamma \beta & \gamma & 0 & 0   \\  0 & 0 & 1 & 0  \\  0 & 0 &0 &1 \end{bmatrix}x = \Lambda x 
$$
我们使用 $\Lambda$ 表示洛伦兹变换阵，$\Lambda^{\mu}_{\nu}$ 表示第 $\mu$ 行第 $\nu$ 列的分量。因此洛伦兹变换的分量式被写成：
$$
\bar x^{\mu}= \Lambda^{\mu}_{\nu} x^{\nu} 
$$
对于两个矢量 $a^{\mu}, b^{\mu}$，变换前后其内积不变。这里的内积是：
$$
a\cdot b = - a^{0}b^{0} + a^{1}b^{1}+a^{2}b^{2} +a^{3}b^{3}
$$
我们玩一些符号上的游戏。我们注意到现在使用的矢量都有上标，我们将这样的矢量称为逆变矢量，而带有下标的矢量则称为协变矢量，它们的关系是：
$$
a_{\mu} = (a_{0},a_{1},a_{2},a_{3}) = (-a^{0},a^{1},a^{2},a^{3})
$$
它们只有一个分量不一样。要想相互转化它们，你可以这样做：
$$
a_{\mu} = g_{\mu \nu } a^{\nu}
$$
$g_{\mu\nu}$ 称为闵可夫斯基度规。

我们已经发现两个四维矢量的点积是洛伦兹变换下的不变量。我们考虑一个四维矢量与其自身的点积 $a^{\mu}a_{\mu}$，如果这个值大于 0，则 $a^{\mu}$ 被称为是类空的；如果等于 0，则称为是类光的；如果小于 0，则称为是类时的。两个事件的间隔记为 $\Delta x^{\mu}  = x_{A}^{\mu} - x_{b}^{\mu}$, $I = (\Delta x)^{\mu} (\Delta x)_{\mu}$ 称为两个事件间的不变间隔。如果 $I$ 是类时的，则可以找到一个参考系使得两个事件发生在同一点；如果 $I$ 是类空的，则可以找到一个参考系使得两个事件发生在同一时刻；如果 $I$ 是类光的，那么两个事件可以被光信号连接。

一个粒子的运动轨迹可以在时空图上使用世界线表示出来。在时空图中，$I$ 相等的面是双曲面（若 $I$ 是类时的，则对应双叶双曲面；反之是单叶双曲面），洛伦兹变换会使得代表事件的点在同一个双曲面上移动。在两个事件的间隔是类时的时候，它们的顺序是绝对的（或者说，洛伦兹变换不会把点从双曲面的一叶变到另一叶）；而类空的时候，两个事件发生的先后顺序则依赖于观测的参考系。因此，为了保持因果律成立，符合物理规律的两个事件的间隔总是类时的。


## 狭义相对论动力学
考虑一个粒子相对于某惯性系 $S$ 以速度 $u$ 运动，则这个粒子上的时钟测得的时间 $\tau$ 与参考系中测得的时间 $t$ 有如下关系：
$$
d \tau = \sqrt{1 - \dfrac{u^{2}}{c^{2}}} dt 
$$
这里的 $\tau$ 称为粒子的固有时。由于 $\tau$ 是在相对粒子静止系中测得的时间，因此它是一个换系不变量，而 $t$ 则随着参考系改变。我们将在参考系 $S$ 中测得的事件间隔对时间的变化率称为粒子的速度：
$$
u = \dfrac{\mathrm{d}I}{\mathrm{d}t}
$$
而事件间隔对固有时的变化率则被称为固有速度：
$$
\eta  = \dfrac{\mathrm{d}I}{\mathrm{d} \tau }
$$
注意到事件间隔 $dI$，或者说 $\Delta x^{\mu}$ 是遵循洛伦兹变换的量，而分母上的 $d \tau$ 则是换系不变量，很容易得知 $\eta$ 遵循洛伦兹变换：
$$
\bar \eta^{\mu} = \Lambda_{\nu}^{\mu} \eta^{\nu}
$$
我们同样定义符合洛伦兹变换的动量：
$$
p = m \eta 
$$
它的第 0 个分量恰好是能量：
$$
E = \dfrac{mc^{2}}{\sqrt{1 - \dfrac{u^{2}}{c^{2}}}} \approx  mc^{2} + \dfrac{1}{2} mu^{2} + \dfrac{3}{8} \dfrac{mu^{4}}{c^{2}} + \cdots 
$$
第一项被称为静能，第二项则是经典力学中的动能。
实验结果指出：根据上面的定义，封闭系统的动量守恒和能量守恒依然成立。有一些小结论，例如 $p$ 和自己的内积：$p^{\mu} p_{\mu} = - m^{2}c^{2}$，以及能量动量三角形 $E^{2} = m^{2}c^{4} + p^{2}c^{2}$。
这里动量和能量的表达式也预示着：可以有一种无质量的粒子以光速前进，它的动量和能量关系是 $E = pc$。

相对论情况下的牛顿第二定律仍然写为：
$$
F = \dfrac{\mathrm{d}p}{\mathrm{d}t}
$$
考虑外力 $F$ 对粒子做的功：
$$
W = \int F \cdot dI  = \int \dfrac{\mathrm{d}p}{\mathrm{d}I} \dfrac{\mathrm{d}I}{\mathrm{d}t} dt  = \int \dfrac{\mathrm{d}p}{\mathrm{d}t} u dt 
$$
其中：
$$
\dfrac{\mathrm{d}p}{\mathrm{d}t} \cdot u  = \dfrac{\mathrm{d}}{\mathrm{d}t} \left(\dfrac{mu}{\sqrt{1 - \dfrac{u^{2}}{c^{2}}}}\right) \cdot  u =  \dfrac{\mathrm{d}}{\mathrm{d}t} \left(\dfrac{mc^{2}}{\sqrt{1 - \dfrac{u^{2}}{c^{2}}}}\right)  = \dfrac{\mathrm{d}E}{\mathrm{d}t}
$$
从而，功能关系依然保持成立：
$$
W = E_{final}  -E_{initial}
$$
牛顿第三定律在相对论中一般不成立（这是因为同时的相对性），只有两个物体接触时（施力点在同一点），牛顿第三定律才成立。因为力是四维动量对 $t$ 的导数，而不是对固有时的导数，因此力也会出现一些千奇百怪的性质。例如可以推导出力的变换：
$$
\bar F_{y} = \dfrac{\mathrm{d} \bar p_{y}}{\mathrm{d} \bar t } = \dfrac{F_{y}}{\gamma\left(1 - \dfrac{\beta u_{x}}{c}\right)}
$$
$F_{z}$ 的变换和 $F_{y}$ 一样，而：
$$
\bar F_{x} = \dfrac{F_{x} - \beta( u \cdot F)/c}{1-\beta u_{x}/c}
$$
为了避免这些复杂的变换，我们可以引入四维力：
$$
K^{\mu} = \dfrac{\mathrm{d}p^{\mu}}{\mathrm{d}\tau}
$$
它与 $F$ 的关系是 $K = \dfrac{1}{\sqrt {1 - \dfrac{u^{2}}{c^{2}}}}F$ ，第 $0$ 分量是功率量纲。


## 狭义相对论电动力学
实际上，电动力学的方程已经与狭义相对论吻合。不同的观察者可以在不同参考系中使用麦克斯韦方程组，有些人可能看到电场，有些人可能看到磁场，但是它们预测到的粒子的运动是一致的。我们接下来的内容不是修正麦克斯韦方程组，而是为它们从相对论的角度找一套数学表述。

我们先给一个简单的引入例子：假设我们有带有 $\lambda$ 电荷的（无限长的）线以速度 $v$ 向右移动，又有带有 $- \lambda$ 电荷的线以速度 $v$ 向左移动，两条线是重合的。在地面系中，一个速度为 $u$ 的粒子离两条线距离为 $s$，正在向右运动。在地面系中，粒子处显然没有电场，粒子受到的力来自于电流 $2 \lambda v$ 产生的磁场。但是，假如我们在粒子系中看，我们可以通过洛伦兹速度变换计算两根线的速度（显然，速度不同），又由于电荷守恒和尺缩效应，此时两条线所带的总电荷量是：
$$
\lambda_{tot} =  - \dfrac{2 \lambda u v}{c^{2} \sqrt{1 - \dfrac{u^{2}}{c^{2}}}}
$$
在粒子系中使用 $\bar F = qE$，并使用一次力变换 $F = \sqrt{1 - \dfrac{u^{2}}{c^{2}}} \bar F$，计算出的结果与直接在地面系中计算洛伦兹力的结果一致。因此，为了保证粒子系和地面系观测的结果一致，在地面系中必须有一个场给粒子施力，这个场就是磁场。

接下来我们仍然通过一些简单的思想实验推出电磁场的变换规律。考虑在 $S_{0}$ 系中静止的平行板电容器，我们同时在 $S_0$ 系和相对于 $S_{0}$ 系向右以速度 $v_{0}$ 运动的 $S$ 系中考虑。在 $S_{0}$ 系中电场可以被立刻写出：
$$
E_{0}  = \dfrac{\sigma_{0}}{\epsilon_{0}} \hat y 
$$
而在 $S$ 系中，由于尺缩效应，$\sigma = \gamma_{0} \sigma_{0}$，因此
$$
E^{\perp} = \gamma_{0} E_{0}^{\perp}
$$
这里垂直符号代表我们研究的电场与相对运动方向垂直。假如我们将电容器横过来放，那么收缩的就是电容器两极板的间距，但场强显然不依赖于这个间距，因此：
$$
E^{\parallel} = E_{0}^{\parallel}
$$
现在我们来看磁场。在 $S$ 系中，电容器的上下极板运动形成电流，很容易计算其磁场为
$$
B_{z}=  - \mu_{0} \sigma v_{0}
$$
我们再考虑一个相对于 $S$ 以速度 $v$ 运动的 $\bar S$ 系，它相对于 $S_{0}$ 系运动的速度为 $\bar v$，则在 $\bar S$ 系中：
$$
\bar E_{y} = \dfrac{ \bar \sigma}{\epsilon_{0}} \quad \bar B_{z} = - \mu_{0} \bar \sigma \bar v
$$
通过简单的计算可以得到：
$$
\bar E_{y} = \left(\dfrac{\bar \gamma}{\gamma_{0}}\right) \dfrac{\sigma}{\epsilon_{0}} \quad  \bar B_{z} = - \left(\dfrac{\bar \gamma}{\gamma_{0}}\right)\mu_{0}\sigma \bar v 
$$
而：
$$
\dfrac{ \bar \gamma}{\gamma_{0}} = \gamma\left(1 + \dfrac{vv_{0}}{c^{2}} \right) \quad  \gamma= \dfrac{1}{\sqrt {1 - \dfrac{v^{2}}{c^{2}}}}
$$
通过配凑，我们可以给出下面的变换公式：
$$
\bar E_{y} = \gamma(E_{y} - v B_{z}) \quad \bar B_{z} = \gamma\left(B_{z} - \dfrac{v}{c^{2}}E_{y}\right)
$$
将电容器横过来，与 $xy$ 平面平行，可以使用类似的方式得到 $\bar E_{z},\bar B_{y}$ 的表达式：
$$
\bar E_{z} = \gamma(E_{z} + v B_{y}) \quad  \bar B_{y} = \gamma\left(B_{y} + \dfrac{v}{c^{2}} E_{z}\right)
$$
前面我们已经推出 $\bar E_{x} = E_{x}$，但是我们现在还差 $B_{x}$ 的变换，这可以通过考虑一个沿着 $x$ 轴放置的螺线管来解决：设螺线管在 $S$ 系中静止，则它产生磁场 $B_{x}= \mu_{0} n I$，在 $\bar S$ 系中 $\bar n  = \gamma n$，但是由于钟慢效应（随着螺线管一起走的钟变慢），有 $\bar I  = \dfrac{1}{\gamma}I$，因此 $\bar B_{x} =B_{x}$ 。至此，我们获得了所有的变换规则。这里给出两个特殊情况：若 $S$ 系中 $B=0$，那么 $\bar B = - \dfrac{1}{c^{2}} ( v \times \bar E)$；若 $S$ 系中 $E=0$，则 $\bar E = v \times \bar B$。

我们已经看出：电场和磁场不是分开变换的，而是一起变换的！我们如何将其写在一起呢？答案是写进一个二阶张量里面。一个二阶张量在变换时服从规则：
$$
\bar t^{\mu\nu} = \Lambda_\lambda^{\mu} \Lambda_\sigma^{\nu} t^{\lambda \sigma} 
$$
注意：*仔细看！里面有两次求和！这可不是矩阵乘法！*
我们使用一个二阶反对称张量来表示电磁场：
$$
F^{01} = \dfrac{E_{x}}{c}, F^{02} = \dfrac{E_{y}}{c},F^{03} = \dfrac{E_{z}}{c},F^{12}= B_{z},F^{31} = B_{y},F^{23} = B_{x} 
$$
在这样的表示方法下，二阶张量的洛伦兹变换恰好可以符合电磁场变换。当然，如果我们将 $\dfrac{E}{c}$ 换成 $B$，将 $B$ 换成 $- \dfrac{E}{c}$，这个变换也是成立的。我们将这样得到的 $G^{\mu\nu}$ 称为 $F^{\mu\nu}$ 的对偶张量。

现在我们使用相对论的语言重建电动力学。首先我们需要表达源（电荷密度和电流密度）的变换。我们定义固有电荷密度为 $\rho_{0}= \dfrac{Q}{V_{0}}$，其中 $V_{0}$ 是在相对静止系中观测到的电荷微元的体积。而一般的电荷密度和电流密度定义为 $\rho = \dfrac{Q}{V}, J = \rho u$，显然：
$$
\rho = \rho_{0}\dfrac{1}{\sqrt{1 - \dfrac{u^{2}}{c^{2}}}} \quad  J = \rho_{0} \dfrac{u}{\sqrt{1 - \dfrac{u^{2}}{c^{2}}}}
$$
$\rho_{0}$ 是换系不变量，因此我们可以构造四维电流密度矢量 $J^{\mu} - (c\rho,J_{x},J_{y},J_{z})$。此时，原本的电流连续性方程 $\nabla \cdot J = - \dfrac{\partial \rho}{\partial t}$ 直接变成：
$$
\dfrac{\partial J^{\mu}}{\partial x^{\mu}} = 0
$$
麦克斯韦方程组被写成两条：
$$
\dfrac{\partial F^{\mu\nu}}{\partial x^{\nu}} = \mu_{0}J^{\mu}  \quad  \dfrac{\partial G^{\mu\nu}}{\partial x^{\nu}} = 0 
$$
可以验证，第一条方程代表着 $\nabla \cdot E = \dfrac{1}{\epsilon_{0}}\rho$ 和 $\nabla \times B = \mu_{0} J + \mu_{0}\epsilon_{0} \dfrac{\partial E}{\partial t}$，第二条则代表着 $\nabla \cdot B = 0$ 和 $\nabla \times E = - \dfrac{\partial B}{\partial t}$。
容易验证，作用在粒子上的力可以写成：
$$
K^{\mu} = q \eta_{\nu}F^{\mu\nu}
$$
写成矢量式，就是：
$$
K = \dfrac{q}{\sqrt{1 - \dfrac{u^{2}}{c^{2}}}} [E + (u \times B)]
$$
最后，我们可以构建四维势：$A^{\mu} = \left(\dfrac{V}{c},A_{x},A_{y},A_{z}\right)$。可以验证，电磁场张量被写为：
$$
F^{\mu\nu} = \dfrac{\partial A^{\nu}}{\partial x_{\mu} } - \dfrac{\partial A^{\mu}}{\partial x_{\nu}}
$$
同样我们可以表示出 $G^{\mu\nu}$，可以验证，$\dfrac{\partial G^{\mu\nu}}{\partial x^{\nu}} = 0$ 在这个写法下自动成立，因此我们只需关注第一条方程：
$$
\dfrac{\partial }{\partial x_{\mu}}\left(\dfrac{\partial A^{\nu}}{\partial x^{\nu}}\right) - \dfrac{\partial }{\partial x_{\nu}}\left(\dfrac{\partial A^{\mu}}{\partial x^{\nu}}\right) = \mu_{0}J^{\mu} \quad (\star)
$$
从 $F^{\mu\nu}$ 的表达式可以看出，我们在 $A^{\mu}$ 上增加一个标量场的梯度，是不改变电磁场的。因此，我们可以进行规范变换。考虑洛伦兹规范：
$$
\nabla \cdot A = - \dfrac{1}{c^{2}} \dfrac{\partial V}{\partial t}
$$
在现在的表示方法下被写为 $\dfrac{\partial A^{\mu}}{\partial x^{\mu}} = 0$，那么在洛伦兹规范下，$(\star)$ 式被化简为：
$$
\square^{2}A^{\mu} = - \mu_{0}J^{\mu} \quad  \square^{2} = \dfrac{\partial }{\partial x_{\nu}} \dfrac{\partial }{\partial x^{\nu}} = \nabla^{2} - \dfrac{1}{c^{2}} \dfrac{\partial ^{2}}{\partial t^{2}}
$$
这就是用四维矢量形式表达的麦克斯韦方程，也就是它最优雅的形式！至此，经典电动力学达到了它的顶峰。