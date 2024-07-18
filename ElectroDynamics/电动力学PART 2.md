#ElectroDynamics 

## 电磁场的能量
我们接触到的第一条守恒定律是电荷守恒（也称为连续性方程）：
$$
\dfrac{\partial \rho}{\partial t} = - \nabla  \cdot J
$$
注意，我们推出麦克斯韦方程组的时候也使用了这条守恒律。因此这不是一个孤立的假设，而是电动力学的基本规律之一。

在之前，我们已经学习过电磁场的能量密度：
$$
u = \dfrac{1}{2}\left(\epsilon_{0}E^{2}+ \frac{1}{\mu_{0}} B^{2}\right)
$$
现在我们的问题是：我们有电荷 $q$，在外场 $E, B$ 下以速度 $v$ 运动了一段时间 $dt$，问外场对它做的功是多少？显然：
$$
F \cdot dl = q (E + v \times B) \cdot v dt = qE \cdot v dt
$$
现在我们考虑一个体积 $V$ 内的电荷：
$$
\dfrac{\mathrm{d}W}{\mathrm{d}t} = \int_{V} qE \cdot v d\tau = \int_{V}(E \cdot J) d \tau 
$$
这是外场在 $dt$ 时间内对区域 $V$ 内的电荷做的功，或者说，是外界“送进”这个区域内的能量。我们希望这个结果中只包含 $E,B$，那么我们使用 Maxwell 方程消去 $J$：
$$
E \cdot J  = \dfrac{1}{\mu_{0}} E \cdot(\nabla  \times B)  - \epsilon_{0} E \cdot  \dfrac{\partial E}{\partial t}
$$
改写其中的一项：
$$
E \cdot (\nabla  \times B) = - B  \cdot  \dfrac{\partial B}{\partial t} - E \cdot (\nabla \times B)
$$
并且凑一下全微分，上面的式子就会变成：
$$
\dfrac{\mathrm{d}W}{\mathrm{d}t} = - \dfrac{\mathrm{d}}{\mathrm{d}t} \int_{V} \dfrac{1}{2}\left(\epsilon_{0}E^{2} + \dfrac{1}{\mu_{0}}B^{2}\right)  d \tau  - \dfrac{1}{\mu_{0}}\oint_{S} (E \times B) \cdot da
$$
这个式子被称为坡印廷定理。它的物理意义是：单位时间内对体积 $V$ 内电荷做的功，等于体积 $V$ 内电磁场能量的减少，减去从体积 $V$ 内流出的能量。因此，我们可以给出单位时间内、单位面积上被电磁场携带的能量（能流密度矢量）：
$$
S = \dfrac{1}{\mu_{0}} (E \times B)
$$
对于我们所关心的区域中没有电荷的情况，坡印廷定理可以退化。我们也可以写出它的另一种写法：
$$
\dfrac{\partial u}{\partial t} = - \nabla \cdot S
$$
这是能量的连续性方程。

## 电磁场的动量
如果将两个运动的电荷限制在轨道上，一个在 $x$ 轴上运动，而另一个在 $y$ 轴上运动，我们会发现二者之间的作用力并不是等大反向的。这违反了牛顿第三定律（或者说，动量守恒）吗？这是因为电磁场也有动量。只有将电磁场的动量和粒子的动量加在一起，我们才能得到系统（守恒的）总动量。

为了研究这一点，我们计算体积 $V$ 中电荷在外场 $E,B$ 下所受的力：
$$
F =  \int_{V} (\rho E + J  \times B) d \tau 
$$
考虑作用在单位体积上的力，同样，我们希望将 $\rho$ 和 $J$ 消去。于是我们有：
$$
f = \epsilon_{0} (\nabla \cdot E)E + \left(\dfrac{1}{\mu_{0}}\nabla \times B  - \epsilon_{0} \dfrac{\partial E}{\partial t}\right)\times B
$$
利用偏导数的运算规则和麦克斯韦方程组，上式中的一部分可以被改写为：
$$
\dfrac{\partial E}{\partial t} \times B = \dfrac{\partial }{\partial t}(E \times B) + E \times (\nabla  \times E)
$$
那么：
$$
f = \epsilon_{0}[(\nabla \cdot E) E -  E \times (\nabla \times E)] - \dfrac{1}{\mu_{0}}[B \times (\nabla \times B)] - \epsilon_{0} \dfrac{\partial }{\partial t} (E \times B)
$$
利用运算规则：
$$
\nabla (E^ {2}) = 2 (E \cdot \nabla )E + 2 E \times (\nabla  \times E)
$$
处理 $E \times (\nabla \times E)$ 和 $B \times (\nabla \times B)$，并且向式子里面添加一个等于 0 的项 $(\nabla \cdot B) B$，上式就变成：
$$
f = \epsilon_{0}[(\nabla \cdot E)E + (E \cdot \nabla )E] + \dfrac{1}{\mu_{0}}[(\nabla \cdot B)B +(B \cdot \nabla ) B] - \dfrac{1}{2}\nabla \left(\epsilon_{0} E^{2} + \dfrac{1}{\mu_{0}}B^{2}\right) - \epsilon_{0} \dfrac{\partial }{\partial t}(E \times B)
$$
这个式子太繁杂，我们使用麦克斯韦应力张量来简化书写，令：
$$
T_{ij} = \epsilon_{0}\left(E_{i}E_{j} - \dfrac{1}{2} \delta_{ij} E^{2}\right) + \dfrac{1}{\mu_{0}} \left(B_{i}B_{j} - \dfrac{1}{2} \delta_{ij}B^{2}\right)
$$
上式可以被简化写为：
$$
f = \nabla \cdot T  - \epsilon_{0} \mu_{0} \dfrac{\partial S}{\partial t}
$$
因此，作用在体积 $V$ 内的力总共就是：
$$
F = \oint_{S} T \cdot da  - \epsilon_{0} \mu_{0} \dfrac{\mathrm{d}}{\mathrm{d}t} \int_{V}S d\tau 
$$
对于静电场、静磁场的情况，第二项为 0.
我们知道，牛顿定律实际上说的是 $F = \dfrac{\mathrm{d}p_{mech}}{\mathrm{d}t}$，那么上面的式子可以写成：
$$
\dfrac{\mathrm{d}p_{mech}}{\mathrm{d}t} = \oint_{S} T \cdot da  - \epsilon_{0} \mu_{0} \dfrac{\mathrm{d}}{\mathrm{d}t} \int_{V}S d\tau 
$$
式子右边的第二项是储存在场中的动量，也就是说，场的动量密度是：
$$
g = \mu_{0}\epsilon_{0}S
$$
而单位时间内被运出区域 $V$ 的动量就是第一项。如果区域 $V$ 内的机械动量 $p_{mech}$ 不变，我们就得到了动量的连续性方程：
$$
\dfrac{\partial g}{\partial t} = \nabla \cdot T
$$
此外，我们自然地得到角动量密度：
$$
l = r \times g  = \epsilon_{0}[r \times (E \times B)]
$$
